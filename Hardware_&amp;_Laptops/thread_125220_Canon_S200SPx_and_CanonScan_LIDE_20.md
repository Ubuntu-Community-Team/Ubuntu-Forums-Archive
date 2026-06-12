---
title: "Canon S200SPx and CanonScan LIDE 20"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by Mishal on 2006-02-03
I can't get either of them to be recognized. Searched google and this forum for links to drivers...but no progress. And I thought my printer is so common that someone or the other must have faced this problem before I did:???: 

Anyway, can anyone help? Thanks...

---

### Post by Zimmer on 2006-02-03
from here
[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)
 Canon S200
  PPD/Driver  bjc-s200
Supported=No
Works? = Yes
Needs cupsys-driver-gimpprint from universe repository 

See this for the bad news on the scanner 
[https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)

I have a Lide 30 which just works..

Have you tried attaching the scanner and trying 
Applications>Graphics>Xsane Image Scanning program to see if it can find the device?
[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)
This site reckons it is supported by the same driver as the Lide 30 
Hope this helps

Regards

---

### Post by Mishal on 2006-02-04
Thanks but I ended up getting both the scanner and the printer automatically detected.

I am astounded by my own stupidity...to be honest:
1) Scanner - I forgot to plug it in with the computer....as soon as I did, XSane detected it.
2) Printer - all I had to do was go to Administration--->Printers---->New Printer and again the Canon S200 was detected automatically.

Silly me...

Thanks for the help though...

By the way, I wanted to ask how I can adjust the quality of the print with this driver. With the manufacturer driver in Windows, I could choose among "High", "Standard" and "Super Economy". Is there anyway of doing that here?

---

### Post by Zimmer on 2006-02-05
[QUOTE=Mishal]

By the way, I wanted to ask how I can adjust the quality of the print with this driver. With the manufacturer driver in Windows, I could choose among "High", "Standard" and "Super Economy". Is there anyway of doing that here?[/QUOTE]

Just go to Printer properties using the print dialogs in applications. Select the 
Device tab and then you will see a list of options 
Printout mode
Resolution,Quality,Ink Type,Media Type (that's ONE option BTW) 
select these with the cursor and left click and the various resolution / ink options will appear on the right hand pane...

Regards

---

