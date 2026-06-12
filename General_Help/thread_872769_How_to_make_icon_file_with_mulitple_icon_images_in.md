---
title: "How to make icon file with mulitple icon images inside?"
date: 2008-07-28
forum: General Help
---

### Post by MountainX on 2008-07-28
I am on Hardy and I want to make some icons for other platforms where there are multiple icon sizes (32x32, 16x16, etc.) in the file. How do I do that in Ubuntu? I just downloaded Inkscape and I can save separate icon files in each size. How do I make the "windows" style icon files with multiple images in it? Thanks.

---

### Post by ryanhaigh on 2008-07-29
You might want to look at [apt://icoutils]("apt://icoutils")

[http://packages.ubuntu.com/hardy/icoutils](http://packages.ubuntu.com/hardy/icoutils)

> Icoutils is a set of programs that deal with MS Windows icons and cursors. Resources such as icons and cursors can be extracted from MS Windows executable and library files with "wrestool". Conversion of these files to and from PNG images is done with "icotool". "extresso" automates these tasks with the help of special resource scripts. 

---

### Post by MountainX on 2008-07-29
> **ryanhaigh said:**
> You might want to look at [apt://icoutils]("apt://icoutils")

[http://packages.ubuntu.com/hardy/icoutils](http://packages.ubuntu.com/hardy/icoutils)

Thank you. Using your tip I found this help:

[A Quick Way to Create a favicon.ico]("http://hilltopyodeler.com/geeker.php")

There are a number of applications that you can use to create a favicon.ico file. The fastest way I have yet found is to use these command line utilities: imagemagick and icoutils.

    --=[ To install ]=--
    $ sudo apt-get install imagemagick icoutils
    --=[ To create the favicon.ico ]=--
    $ convert yourImage.gif -resize 32x32 favicon.png
    $ icotool -c -o favicon.ico favicon.png 

Unfortunately, I can't tell if that puts multiple size icons in the output file.

---

### Post by MountainX on 2008-07-29
I found more info here: [http://www.tutorgig.com/ed/Favicon](http://www.tutorgig.com/ed/Favicon)

[INDENT]The original means of defining a favicon was by placing a file called favicon.ico in the root directory of a web server. This would then automatically be used in Internet Explorer's favorites (bookmarks) display. Later, however, a more flexible system was created using HTML to indicate the location of an icon for any given page. This is achieved by adding two link elements in the <head> section of the document as detailed below. In this way any appropriately sized (16×16 pixels or larger) image can be used and, although many still use the ICO format, other browsers (though not all versions of Microsoft's Internet Explorer) now also support the PNG and animated GIF image formats.[/INDENT]

It is almost sounding like I don't need to be so concerned with the .ico format. Maybe I should just make a 32x32 PNG image...

---

### Post by ryanhaigh on 2008-07-29
If you are only using this as a favicon then as you say you don't actually need to have a .ico file although I don't understand why you would want different sizes in the one image if all you are doing is creating the favicon.

---

### Post by MountainX on 2008-07-29
> **ryanhaigh said:**
> If you are only using this as a favicon then as you say you don't actually need to have a .ico file although I don't understand why you would want different sizes in the one image if all you are doing is creating the favicon.

I thought a favicon was supposed to have different sizes in one file so that it would display well on many different screen resolutions. The person browsing to the site could have any screen resolution.

I appreciate any advice.

---

### Post by ryanhaigh on 2008-07-29
Wikipedia simply says 16x16 or larger: [http://en.wikipedia.org/wiki/Favicon](http://en.wikipedia.org/wiki/Favicon)

The favicon is only shown in the address bar/firefox bookmarks where its size remains small. Even on high resolution screens the size of the favicon is dependent on how the apps display it and all the ones I know keep it very small so even if you provide a larger image it will remain small.

Wikipedia uses a favicon.ico with a single small size: [http://en.wikipedia.org/favicon.ico](http://en.wikipedia.org/favicon.ico)

---

### Post by MountainX on 2008-07-30
ryanhaigh - thanks again.

I also found this link that is pretty good:
[http://perishablepress.com/press/2007/10/17/everything-you-ever-wanted-to-know-about-favicons/](http://perishablepress.com/press/2007/10/17/everything-you-ever-wanted-to-know-about-favicons/)

"favicons are square images that typically are seen in sizes of 16×16 and 32×32, as measured in pixels. Although 64×64 and even larger sizes are possible, browser support is inconsistent for anything greater than 16×16. Generally, 16×16 favicons are more than sufficient, however some browsers such as Microsoft’s Internet Explorer may display favicons at 32×32 for sites bookmarked in favorites."

I never use IE, but visitors to my site probably will (unfortunately).

For the moment, however, I'm just going to use Gimp to make a 16 x 16 .ico file.

---

