# jquery-ui-tooltip-altposition

jQuery UI Tooltip which alters position according to the situation.  
The default position is under the element. It looks best position. But, it is not sometimes.  
For example, it overlap pulldown list of `select`, or it is too lower position under the high `textarea`.  
![jQuery UI Tooltip](sample1.png)

This alters position by specified conditions. (e.g. height, tag-name)  
[Demo](http://jsfiddle.net/uyyxh/)

## Usage

Load the `jquery.ui.tooltip.altposition.js` script file after loading `jquery.ui.tooltip.js` etc.

```html
<link rel="stylesheet" type="text/css" href="//ajax.googleapis.com/ajax/libs/jqueryui/1.10.3/themes/blitzer/jquery-ui.css" />
<script type="text/javascript" src="//ajax.googleapis.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>
<script type="text/javascript" src="//ajax.googleapis.com/ajax/libs/jqueryui/1.10.3/jquery-ui.min.js"></script><!-- jquery.ui.tooltip.js is included -->
<script type="text/javascript" src="/path/to/jquery.ui.tooltip.altposition.js"></script>
```

The `altPosition` Object is added to Tooltip options.  
The position is altered to `altPosition.position` ([jQuery UI Position](http://api.jqueryui.com/position/) Object) when any following conditions.

+ The tag-name of the element is `altPosition.tagName`.
+ `outerWidth` of the element is greater than or equal to `altPosition.minOuterWidth`
+ `outerWidth` of the element is less than or equal to `altPosition.maxOuterWidth`
+ `outerHeight` of the element is greater than or equal to `altPosition.minOuterHeight`
+ `outerHeight` of the element is less than or equal to `altPosition.maxOuterHeight`
+ `altPosition.callback` Function returns `true`

*NOTE:* These are joined by *OR*. (The position is altered if one or more conditions.)

## Example

```js
$('input,textarea,select').tooltip({
  altPosition: {
    minOuterHeight: 60,
    tagName: 'select',
    callback: function() { return this.element.val().length > 20; },
    position: {my: 'left+15 top', at: 'right top', collision: 'flipfit'} // Right side
  }
});
```
