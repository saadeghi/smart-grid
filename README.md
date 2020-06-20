# Smart Grid Sass Mixin
Smart and minimal Sass grid mixin that doesn't need HTML class names!  

⚠️ This mixin works with `display:inline-block` and it was a solution for old browser that doesn't support `flexbox` and `CSS grid`. Since all modern browsers support `CSS grid` now, I suggest that you don't use this mixin and use `CSS grid` instead.   


```html
<div class=grid>
	<div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
	</div>
</div>
```
```scss
// 3 columns in a row with equal width
.grid{
	@include smartgrid( 1/3 );
}
```
## Advanced usage

```scss
// coulmn width: 20%
 .grid{
	@include smartgrid( .2 );
}
```
```scss
// first column: 20%
// second column: 40%
// third column: 40%
.grid{
	@include smartgrid(
		[ 1/5, 2/5, 2/5 ]
	);
}
```
```scss
// first column: 25%
// second column: 75%
// 15px gap between columns
.grid{
	@include smartgrid(
		[ .25, .75 ],
		[15]
	);
}
```
```scss
// first column: 30%
// second column: 70%
// 10px gap between columns (margin-right)
// 10px gap between rows (margin-bottom)
.grid{
	@include smartgrid(
		[ 3/10, 7/10 ],
		[10 10]
	);
}
```
```scss
// 10px gap between columns (margin-right)
// 10px gap between rows (margin-bottom)
// When screen resolution is more than 480px:
//	 first column: 25%
//	 second column: 50%
//	 third column: 25%
// For smaller screens:
//	 all columns: 50%
.grid{
	@include smartgrid(
		[
			["480px",[ 1/4 2/4 1/4 ]]
		],
		[10 10],
		1/2
	);
}
```
```scss
// 10px gap between columns (margin-right)
// 10px gap between rows (margin-bottom)
// When screen resolution is more than 480px:
//	 all column: 50% (.5)
// When screen resolution is more than 960px:
//	 all column: 33.3% (.3)
// When screen resolution is more than 1200px:
//	 all column: 20% (.2)
// Default width:
//	 all columns: 20% (1/5)
.grid{
	@include smartgrid(
		[
			["480px",[ .5 .5 .5 ]],
			["960px",[ .3 .3 .3 ]]
			["1200px",[ .2 .2 .2 ]]
		],
		[10 10],
		1/5
	);
}
```
