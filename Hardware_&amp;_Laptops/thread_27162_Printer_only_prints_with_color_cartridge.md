---
title: "Printer only prints with color cartridge"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by Gustav on 2005-04-15
My printer (hp psc 1110) won't use the black cartridge when printing black stuff, it always use the color cartridge. 

I have used the printer administration tool to set it to only print greyscale with the black cartridge but it still only uses color.

Do anyone have a solution for this problem?

---

### Post by Bob D. on 2005-04-17
Have you tried this printer on another PC? This sounds more like a printer problem than a OS problem.

Please post back and we will take it from there.

Cheers.

Bob

---

### Post by Gustav on 2005-04-18
It works in windows

---

### Post by Bob D. on 2005-04-18
Well, I'm at a loss on this one. Been doing some reading at the LinixPrinting website ([http://www.linuxprinting.org/](http://www.linuxprinting.org/)) and can't find any reason for this to happen. There is apparently a newer colorspace (KRGB) that enhances black printing and line art, but Ubuntu has the patch already in a normal install. The PSC1100 (1110) is fully supported by the hpijs printer driver. I use a PSC2710 and print via wireless, both black and color, without problem with the hpijs driver.

Best suggestion I could make would be to post your question to the HP forum at LinuxPrinting.org. Since your problem is a bit obscure, I doubt you are going to get the help you need here. HP support staff do monitor and reply in the HP forum at the LinuxPrinting site.

Sorry I could not be of more assistance. If you do receive an answer, please do post back here so the rest of us can learn from you experience.

Cheers,

Bob

---

### Post by Gustav on 2005-04-18
Thank you for your help anyway

---

### Post by Gustav on 2005-04-25
Now it works in OpenOffice but not in gedit :|

---

### Post by simius on 2005-10-02
How did you get it to work in OpenOffice.org? Or did you fix the entire problem? I'm having the same problem with my HP PSC 1215, using Breezy.

---

### Post by David Haas on 2005-10-02
Gustav--I'm interested in knowing whether you set up your printer with the Gnome printer manager in Ubuntu, and whether you selected the PPD file "HP-PSC_1100-hpijs.ppd.gz" in the HP directory at "/usr/share/cups/model/foomatic-ppds/HP"? Also, is an unzipped copy of this file now present at /etc/cups/ppd?
David

---

### Post by tomwell on 2005-12-09
I seem to be having the same problem with a psc 1210... Any news about printing black using the "black Cartdrige...??"

Peace

Tom

---

### Post by RacoonBerry on 2006-01-21
Ditto here using HP PSC 1210. I should have checked here before I replaced my black ink cartridge. :(

---

### Post by galgoz on 2006-01-28
I am having the same issue.  I have the print server on a ubuntu computer.  When I print from another ubuntu computer it only uses the color cartridge.  When I print from windows it does black only like I want it too.  Makes me sick that windows is handling this better.

---

