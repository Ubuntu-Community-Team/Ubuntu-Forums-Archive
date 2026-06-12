---
title: "Pixma IP3000 printer resolution not correct"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by Arcturus691 on 2008-01-08
Hello,
I am having problems with the resolution of my Canon Pixma IP3000 printing photos. The printer prints black and white fine and it prints in color.  The printer does not print photos anywhere near the printers maximum resolution.  I am comparing this to the photo print quality on windows XP.  

I am starting this thread because I have read many of the threads involving this printer, including how to's.   I have found many solutions that I do not consider workable (in my opinion) so far as for photo printing.  I can download linux drivers from Canon's Japanese ftp, however many people have reported that the colors are wrong or that all the functionality is not supported.  This does not surprise me because the firmware is different between models in different countries as far as I know.
  
--** I can print photos but they come out grainy.**  
I think the problem is that if you look in the printer configuration the resolution is set to 600X600(that is the only option), but I could be wrong.  I also set cups to the paper that I am using.

--**The colors are not correct** (but they look correct on the monitor)


Actual resolution according to Canon
Black: 600 x 600 dpi
Color: 4800 x 1200 dpi

How do I set the printer to the color resolution to 4800 X 1200 or suitable photo res?
Is 600 X 600 dpi a limitation of the driver listed below?

Cups config:
Media Size:  4X6
Color Model: RGB Color	
Media Type: Glossy Photo Paper
Media Source: Auto Sheet Feeder	
Resolution: 600X600
Ink Type: CMYK
Image Type: Photograph
Printer Driver: Canon PIXMA iP3000 - CUPS+Gutenprint v5.0.1 Simplified

Additional Info:
x86 32bit Gutsy 7.10
Using gimp and f-spot photo to print

Any help would be greatly appreciated :)

Update:
Found out from the /usr/share/gutenprint/5.0.1/xml/printers.xml file that the canon pixma ip3000 uses the ip4000 parameters and if you look on [http://gutenprint.sourceforge.net/p_Supported_Printers.php3](http://gutenprint.sourceforge.net/p_Supported_Printers.php3) you will find that the pixma ip4000 is supported but in the notes section it states that is [COLOR="DarkRed"]experimental[/COLOR].  I was under the incorrect impression that the ip3000 was fully supported.

---

### Post by Arcturus691 on 2008-01-20
Bump?:-k

---

### Post by Bendemann on 2008-01-20
I don't know any driver that supports this high resolution. Did you try Turboprint?

---

### Post by Arcturus691 on 2008-01-23
Bendemann, Thanks for the reply,
No I have not tried Turboprint, from what I have read it might fix my problem for a cost of $40. There is a trial version but it puts a banner on anything you print out in high res.  Not a bad price but more then I have to spare currently. I will try it out when I get a chance.
Thanks for the tip :)

---

### Post by rjs987 on 2008-04-10
This is the very same printer I have, but no longer have connected. I just recently moved over from Windows to Kubuntu 7.10. My Windows box is still running as I finish converting some data to Linux. I found that none of the Pixma series is fully supported and all indication of support is experimental. I ended up using a BJC7000 driver in CUPS to print decent text, but was unable to print any photo correctly. I kept looking for a solution but found none that worked for me with the Canon printer. I also have a Visioneer scanner also. Visioneer is not at all supported on Linux. So I needed a solution to both problems. You may not like my solution but here it is anyway... I replaced both printer and scanner with an HP Photosmart c6280 all-in-one and found that this is fully supported with HPLIP. I really like Canon printers but they just are not supported well so I can't use them. The HP does very well with scanning, printing, and photos. Color and resolution is great, and b/w text prints are at least as good as the Canon put out.

Now, if I can just get rid of the 1/8 inch border around my 4x6 photo prints.

Edit 2008.04.11: I finally got rid of the border! Was easier than I thought it would be but was a setting I didn't know where to find. I just kept looking. I am planning a new post to detail how I did it.

---

