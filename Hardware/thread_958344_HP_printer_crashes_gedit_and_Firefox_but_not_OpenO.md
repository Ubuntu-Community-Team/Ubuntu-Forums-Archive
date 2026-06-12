---
title: "HP printer crashes gedit and Firefox but not OpenOffice"
date: 2008-10-25
forum: Hardware
---

### Post by DarrenCarlton on 2008-10-25
When I'm try to print from Firefox, gedit, F-spot, et al, the applications hang and never come back to life. When I try to print from OpenOffice or Audacity (an audio application), I have no problems at all.

Here are the steps to reproduce:
1. Open gedit and type some text.
2. Select File > Print.
3. gedit goes gray and never responds.
   When I try to print from Firefox, the Print
   dialog box displays, but it's gray and has no content. And
   Firefox itself is gray and never responds.
4. From the desktop, choose System > Adminstration > Printing and remove the HP printer.
5. Reopen gedit and try to print.
6. Gedit displays the print dialog box with the open to print to file.

But I have no problem printing from OpenOffice.

Configuration info:
Ubuntu 8.04.1
Firefox 3.0.3
Hplip 2.8.9
Device Manager version 15.0

Output from sudo hp-check -r says everything's OK except for " SIP not installed or version not found."

I changed the CUPS server to output debug messages. I'll attach an annotated copy of the output.

---

