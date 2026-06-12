---
title: "CUPS Blurry graphics with LP 2844-Z label printer"
date: 2012-10-23
forum: Hardware
---

### Post by aramkolt on 2012-10-23
I've been trying to get my LP 2844-Z shipping label printer (Z means that it uses the ZPL language) to work with two machines, one with Snow Leopard, and one with Mountain Lion.* Ubuntu should use the same CUPS (Common Unix Printing System), which is why I'm posting here.  I set up the printer using the standard ZPL driver.* I am able to print a test page from CUPS at "localhost:631/" and the CUPS test page prints crystal clear text but the CUPS test image is a bit blurry.* Whenever I try to print any sort of image using OSX, I get very blurry images printed.* 

I figured out the reason that text prints clear in some situations and not in others is that the printer only supports certain basic fonts like Helvetica.

What is odd is that the windows drivers for this printer result in crisp images and text regardless of font.  My reasoning says that Windows is able to send all data line by line and the printer just prints the data calculated by the computer instead of trying to scale or dither or however it's distorting the images printed from OSX.  

The driver file is a ppd file named Zebra.ppd which I do not know what parameters might fix this.  Is there some way to tell the printer to print a "post-script" image or "post document format" that the computer calculates as optimal instead of the printer trying to scale the image in a lossy way that is giving me the results I'm seeing?
*
I've tried a few other versions of the zebra.ppd driver that I found online on some ubuntu forums and all have given me the same result.
*
I've gone into CUPS and made sure that the paper/media size are the correct 4x6 inches.
*
I've made sure that the paper size is correctly set to 4x6 inch within OSX and I've even tried scaling images to different native resolutions and 4x6 inch size that the printer uses, but I always get the same blurry printing result.*

I've attached scans of what the output looks like of the CUPS test page printed from OSX and an identical native 4x6 Word document with the Apple Logo and an image of a barcode, one printed from mac and one from windows.* As you can see from the CUPS Test Page, the image there is not very clear either.

A Zebra.ppd file can be found here if anyone wants to take a look at possible parameter changes that could fix this: [http://andis63.homeftp.net/downloads/packages/cups/cups-1.5.0/ppdc/ppd/zebra.ppd](http://andis63.homeftp.net/downloads/packages/cups/cups-1.5.0/ppdc/ppd/zebra.ppd)   I've also attached this file zipped to this post.

Any help or information would be greatly appreciated.  Thanks in advance!

---

