## Website Performance Optimization portfolio project

### Introduction

#### A Portfolio Website is given to which optimization is needed..One of link in that site redirected to pizzeria Website in which optimization in terms of fps is much needed.
	
### How to Load?

##### To Load this project, just clone or download the zip.Open the index.html in any browser.To view the the optimizations,please open the Developer tools in the browser and check the performance.

## PART-1 Optimization of index.html with PageScore of more or equal to 90

### 1) async Javascripts
#####    Added async attributes to the  Google Analytics javascript.
### 2) Web Font Loader Script
#####	 Instead of adding Google Web Fonts with the link tag,for unbloacking the rendering path,an inline javascript is been added in index.html in footer section which enalbes the web fonts.
Script is:
```
<script type="text/javascript">
        WebFontConfig = {
          google: { families: [ 'Open+Sans:400,700'] }
        };
        (function() {
          var wf = document.createElement('script');
          wf.src = ('https:' == document.location.protocol ? 'https' : 'http') +
            '://ajax.googleapis.com/ajax/libs/webfont/1.5.18/webfont.js';
          wf.type = 'text/javascript';
          wf.async = 'true';
          var s = document.getElementsByTagName('script')[0];
          s.parentNode.insertBefore(wf, s);
        })();
      </script>
```

#### For further details, you can refer,https://github.com/typekit/webfontloader

### 3) Stylesheets

##### The link tags for stylesheets style.css and print.css are added in footer section with the Media attributes.They are kept in footer section so that it starts building HTML and atlast goes for styling the HTML DOM with stylesheet.

## PART-2 Optimization in main.js file with 60fps

### 1) DetermineDx and Switch Case Function
#####     In the resizePizzas object, the determineDx and calling it in each iteration of for-loop was FSL. So,to avoid that the switch case which returns the new Width percentage kept in the functional object scope and determine Dx was removed.Due to which,fps increased upto certain level.
### 2) updatePosition();
#####	 2.1) In the function updatePositions(), the phase was calculating the DOM value each and every time in the for loop which finally,I kept outside the forloop.Also,in the further calculation, the modulo operator was removed.
#####	 2.2) logAverageFame() function was again calculating the DOM value with an extra variable. So,that was also removed.
