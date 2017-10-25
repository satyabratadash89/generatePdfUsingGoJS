GoJS, a JavaScript Library for HTML Diagrams
============================================
First run a bower install to install goJS and jsPDF. To include the function to 'save pdf' add the following function.
The save to pdf functionality has been added on genogram.html(samples/genogram.html) as an example.

The function is as follows:
Script:
------
    function generateImages(width, height) {
      width = parseInt(width);
      height = parseInt(height);
      if (isNaN(width)) width = 100;
      if (isNaN(height)) height = 100;
      width = Math.max(width, 50);
      height = Math.max(height, 50);



      var imgDiv = document.getElementById('myImages');
      imgDiv.innerHTML = '';
      var db = myDiagram.documentBounds.copy();
      var boundswidth = db.width;
      var boundsheight = db.height;
      var imgWidth = width;
      var imgHeight = height;
      var p = db.position.copy();
      for (var i = 0; i < boundsheight; i += imgHeight) {
        for (var j = 0; j < boundswidth; j += imgWidth) {
          img = myDiagram.makeImage({
            scale: 1,
            position: new go.Point(p.x + j, p.y + i),
            size: new go.Size(imgWidth, imgHeight)
          });
          img.className = 'images';
          var doc = new jsPDF();
          var image = "data:image/png;base64,iVBORw0KGgoAA..";
          doc.addImage(img, 'JPEG', 15, 40, 180, 160);
          doc.save('genogram.pdf');
        }
      }

    }


    function printImage(){
    	alert("Clicked the button");
        generateImages(1200, 1280);
        
    }

Button to call the function:
----------------------------
<button onclick="printImage()">Generate PDF</button>




----------------------------------------------------------------------

<img align="right" height="150" src="https://www.nwoods.com/images/go.png">

[GoJS](https://gojs.net) is a JavaScript and HTML5 library for creating interactive diagrams, charts, and graphs.

[See GoJS Samples](https://gojs.net/latest/samples).

[Get Started with GoJS](https://gojs.net/latest/learn)

Read more about GoJS at [gojs.net](https://gojs.net)

This repository contains both the library and the sources for all samples, extensions, and documentation.
You can use the GitHub repository to quickly [search through all of the sources](https://github.com/NorthwoodsSoftware/GoJS-Samples/search?q=setDataProperty&type=Code).


<h3>Support</h3>

Northwoods Software offers a month of free developer-to-developer support for GoJS to help you get started on your project.

Read and search the official <a href="https://forum.nwoods.com/c/gojs">GoJS forum</a> for any topics related to your questions.

Posting in the forum is the fastest and most effective way of obtaining support for any GoJS related inquiries.
Please register for support at Northwoods Software's <a href="https://www.nwoods.com/products/register.html">registration form</a> before posting in the forum.

For any nontechnical questions about GoJS, such as about sales or licensing,
please visit Northwoods Software's <a href="https://www.nwoods.com/contact.html">contact form</a>.


<h3>License</h3>

The GoJS <a href="https://gojs.net/latest/doc/license.html">software license</a>.

Copyright (c) Northwoods Software Corporation