---
title: "HP Photosmart C5180 printing Photos"
date: 2008-07-15
forum: Hardware
---

### Post by Paul Earland on 2008-07-15
Hello.
Using Ubuntu with a HP Photosmart C5180 Printer. How do I print from computer from stored photos onto the small photo paper in the top tray? No problem with printing onto the A4 sheets in bottom tray.
Thanks.
Paul

---

### Post by siman on 2008-07-20
same problem here. i have an c5180. i tried different drivers and the hp-print utility as suggestes on linuxprinting.org. 

best case is, i get a printer-error where it says ¨paper size does not match selected tray" and it even feeds in a photo paper, but then i have to press cancel and it gets ejected empty.

i also went through this [http://ubuntuforums.org/showthread.php?t=843010](http://ubuntuforums.org/showthread.php?t=843010)

---

### Post by Slug71 on 2008-07-24
Howd you guys get the printer installed if you dont mind? Im a newbie, just installed Ubuntu yesterday.

---

### Post by ricardisimo on 2008-12-31
Slug,

Did you still need help with the printer install?

---

### Post by ricardisimo on 2008-12-31
Did anyone ever figure out how to print from the photo tray? I get the same paper size error on my 5180.

---

### Post by ricardisimo on 2008-12-31
Got it. In F-Spot, select the photo you want to print, then go to Photo >> Page Setup and in "Format for:" choose "Photosmart_C5100_series". Then in "Paper size:" select "Photo or 4x6 inch index card." Why you have to first choose "C5100_series" is beyond me, because afterwards, this paper size is available for "Any printer." Click "Apply" and then go to Photo >> Print. Under "Page Setup," "Paper Source" choose "Photo tray;" under "Image settings" tick "Full page (no margin);" and on "Advanced" "Printout Mode" should be "Photo (on photo paper)" and for resolution I choose "1200 dpi, Photo, Full Bleed, Black + Color Cartr., Photo Paper." It turns out fantastic on this setting.

Evidently, it's easy enough to set up the 5180 twice - once as the default printer for regular jobs, and a second time as the photo printer, where all of the above can be preset. This would be done under System >> Administration >> Printing. Good luck all.

---

### Post by panicosm on 2009-02-10
Thanks ricardisimo,
Works with F-spot in intrebit as well. Unfortunately does not work with GIMP

---

### Post by b49P23TIvg on 2011-12-23
I've got the HP C7280 All-in-One.
Even f-spot wouldn't work, which I had to install since shotwell is now distributed with my ubuntu version.

I finally taped my envelopes to letter paper and fed through the bottom tray.  And, since I was merely adding decorations I didn't care about the orientation, placement, or scale.  So I can't advise.

The taped pages worked without jamming.

---

