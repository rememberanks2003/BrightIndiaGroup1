# Textrotator

Simple jQuery plugin to rotate text, rotate images (banners), or any other html.


## Installation

Add to head of your html document

```html
<script type="text/javascript" src="jquery.textrotator.min.js" />
```


### Add your html markup

* add different display time duration by adding ```data-duration="1000"``` .  This adds 1s duration
* add different easin and easout easing by adding ```data-easingin="swing" data-easingout="linear"```.
* add random = true to randomize the li elements.

```html
<html>
	<head>
		<script type="text/javascript" src="jquery.textrotator.min.js" />
	</head>
	<style>
		#my-textrotator {list-style: none; padding:0; margin: 0 0 24px;}
		#my-textrotator li {display: none;}
	</style>
	<body>
		<ul id="my-textrotator">
			<li data-duration="10000" data-easingin="swing" data-easingout="linear" >Text 1</li>
			<li>Text 2</li>
		</ul>
	</body>
</html>
```
### Add javascript code for calling the Rotator.
```html
<script type="text/javascript">
	$(function(){
		$('#my-textrotator').textRotator({
			random : false,
			fadein : 1000,
			fadeout : 500,
			duration : 5000,
           	easingin: 'swing',
            easingout: 'swing'		
		})
	})
</script>
```
## Adding Wordpress

### Shortcodes

```
[textrotator]
[tritem duration="5000"  easingin="easeInElastic"]<div style="background-color: red ;margin-top: 6px; padding: 100px 12px; text-align: center;">Slide 1</div>[/tritem]
[tritem duration="10000"]<div style="background-color: blue ;margin-top: 6px; padding: 100px 12px; text-align: center;">Slide 2</div>[/tritem]
[tritem duration="1000" ]<div style="background-color: green;margin-top: 6px; padding: 100px 12px; text-align: center;">Slide 3</div>[/tritem]
[/textrotator]

```

### The functions.php File

```php

add_shortcode('tritem', 'turple_shortcode_tritem');
function turple_shortcode_textrotator($att, $content = null){
	$banner = '<ul class="textrotator" style="list-style: none; padding: 0; margin: 0 0 24px">' . do_shortcode($content) .'</ul>';	
	return __($banner);
}

add_shortcode('textrotator', 'turple_shortcode_textrotator');
function turple_shortcode_tritem($att, $content="null"){	
	return '<li style="display: none" '.
		(isset($att['duration']) ? ' data-duration="'.intval($att['duration']).'" '  : '') .
		(isset($att['easingin']) ? ' data-easingin="'.intval($att['easingin']).'" '  : '') .
		(isset($att['easingout']) ? ' data-easingout="'.intval($att['easingout']).'" '  : '') .
		'>'. do_shortcode($content) . '</li>';
	
}

```

## Errata or Issues
If you find and issues please fill out an Issues request https://github.com/sturple/textrotator/issues
