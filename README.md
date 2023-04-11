# Changing Elements

CSS has a property called transform where a two-dimensional transformation is applied to an element. This property contains a list of transform functions similar to those allowed by SVG. The transform property can be applied to any HTML element and all children elements will inherit the transformation applied to a parent element. I will be trying out several values of the transform property and showcasing their effect. You can refer to [this table](#transformation-values) that summarizes all the values.

## Use Cases

CSS transform is mostly used when we need to affect a change in the shape or position of an HTML element. This change will almost always distinguish the element from the original state in its definition. The **transform** property works well with css animations too, you can read [this article](/article/css-animations) that goes into the basics of animation with CSS. Also, make sure to refer to the [MDN article]() about CSS transform.

The syntax of using transform looks like this:

```CSS
  selector{
    transform: value();
  }
```

Where `value()` is any one of the functions that are accepted by the **transform** property. Refer to the [table below](#transformation-values) for references of each function.

## Examples

To demonstrate how CSS transform works, we need some HTML code to apply the CSS rules to. The following HTML code will serve as a good template:

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Transform Property 🤖</title>
    <link rel="stylesheet" href="styles.css">
</head>

<body>
    <div class="item"></div>
</body>

</html>
```

Then, we can apply the following base CSS rules:

```CSS
*, *::before, *::after{
    padding: 0;
    margin: 0;
}

body{
    height: 100vh;
    width: 100vw;
    overflow: hidden;
}

.item{
    margin: 200px auto;
    width: 30%;
    height: 30%;
    background-color: violet;
    border: 1px solid black;
    border-radius: 10px;
    transition: 0.1s ease-in-out;
}
```

The code samples above will make a violet rectangle in the middle of the browser window:

![A screenshot of the browser window](violet-box.png)

CSS transform is ideally paired with a pseudo-class or animation Key Frames in order to apply a gradual effect. Here is an example of a transformation that increases the elements size when a user places their mouse cursor over the element.

```CSS
.item:hover{
    cursor: pointer;
    transform: scale(1.5);
    border: 3px dotted black;
}
```

It is also possible to apply the transformation definition when a user clicks the element as shown below:

```CSS
.item:active{
    cursor: pointer;
    transform: matrix(0.5, 2, 2.5, 3, 3.5, 4);
    border: 3px dotted black;
}
```

The `skew()` function can be used on the hover state as shown below:

```CSS
.item:hover{
    cursor: pointer;
    transform: skew(20deg);
}
```

Another cool thing we can do is combine two CSS transform functions to apply two rules on an element. For example, we can combine the `scale()` and `skew()` functions on the hover pseudo class as shown below:

```CSS
.item:hover{
    cursor: pointer;
    transform: scale(1.5) skew(20deg);
    border: 3px dotted black;
}
```

Notice how the violet rectangle skews along the X and Y axes as well as increases in size.

## Animations

Using CSS transform as part of animation Key Frames is an ideal way of using it. Alternatively, you could use margin to manipulate movement but that could break the layout of a web page. Using transform ensures that surrounding elements stay in position in addition to the movement. 

Here is an example of applying a CSS animation by utilizing the transform property inside the Key Frames.

**Firstly define the @Key Frames rules**:

```CSS
@keyframes move-side-to-side {
    0%{
        transform: translateX(0);
    }
    50%{
        transform: translateX(50%);
    }
    100%{
        transform: translateX(0);
    }
}
```

**Then apply the animation to the hover pseudo class**:

```CSS
.item:hover{
    cursor: pointer;
    animation: move-side-to-side 0.5s linear infinite;
    border: 3px dotted black;
}
```

This enables the violet rectangle to move from one side to another.

![An image of CSS animations](rectangle-animation)

## Transformation Values

The table below is a summary list of some of the possible values that the CSS transform property can accept.

|Transform Function|Description |
| :---: |:---: |
|`matrix()`|Specifies a 2D transformation in the form of a transformation matrix of six values. matrix(a,b,c,d,e,f) is equivalent to applying the transformation matrix [a b c d e f]|
|`matrix3d()`|Specifies a 3D transformation as a 4x4 homogeneous matrix of 16 values in column-major order.|
|`perspective()`|Specifies a perspective projection matrix.|
|`rotate()`|Specifies a 2D rotation by the angle specified in the parameter about the origin of the element, as defined by the transform-origin property.|
|`rotateX()`|Specifies a clockwise rotation by the given angle about the X axis.|
|`rotateY()`|Specifies a clockwise rotation by the given angle about the Y axis.|
|`rotateZ()`|Specifies a clockwise rotation by the given angle about the Z axis.|
|`scale()`|Specifies a 2D scale operation by the (sx,sy) scaling vector described by the 2 parameters. If the second parameter is not provided, it takes a value equal to the first.|
|`scale3d()`|Specifies a 3D scale operation by the (sx, sy, sz) scaling vector described by the 3 parameters.|
|`scaleX()`|Specifies a scale operation using the (sx, 1) scaling vector, where sx is given as the parameter.|
|`scaleY()`|Specifies a scale operation using the (sy, 1) scaling vector, where sy is given as the parameter.|
|`scaleZ()`|Specifies a scale operation using the (1, 1, sz) scaling vector, where sz is given as the parameter.|
|`skew()`|Specifies a skew transformation along the X and Y axes. The first angle parameter specifies the skew on the X axis. The second angle parameter specifies the skew on the Y axis. If the second parameter is not given then a value of 0 is used for the Y angle (ie: no skew on the Y axis).|
|`skewX`|Specifies a skew transformation along the X axis by the given angle.|
|`skewY`|Specifies a skew transformation along the Y axis by the given angle.|
|`translate()`|Specifies a 2D translation by the vector (tx, ty), where tx is the first translation-value parameter and ty is the optional second translation-value parameter.|
|`translate3d()`|Specifies a 3D translation by the vector (tx, ty, tz), with tx, ty and tz being the first, second and third translation-value parameters respectively.|
|`translateX()`|Specifies a translation by the given amount in the X direction.|
|`translateY()`|Specifies a translation by the given amount in the Y direction.|
|`translateZ()`|Specifies a translation by the given amount in the Z direction. Note that percentage values are not allowed in the translateZ translation-value, and if present are evaluated as 0.|

## Wrapping Up

In this article, I've shown you how the transform property of CSS can be used to change the visible state of an element. Be sure to also read my article about [CSS animations](/articles/css-animations) to learn more about it. I also have another one about [Exploring HTML](/articles/exploring-the-hypertext-markup-language) which is a good beginners tutorial.

Your feedback is welcome through [this link](https://andrew-tech.netlify.app). Lastly, thank you for reading and have a good day!

---

### ~ Thank you for reading

---