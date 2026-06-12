---
title: "Breezy on Inspiron 700m"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by arunvijai on 2006-04-04
Hi All, 

I have just installed Breezy on Inspiron 700m and having some trouble with display. Display is not set to 1280*960 and i have tried editiing manually /etc/X11/xorg.conf 

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
Modeline "1280x960_75.00"  129.86  1280 1368 1504 1728  960 961 964 1002
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1280x960"
EndSubSection
EndSection

Still not getting the display. Can anybody point me how to do it ? 

Thanks,
Arun

---

### Post by arunvijai on 2006-04-05
Any help guys ?

---

### Post by RealGene on 2006-04-07
](*,) 
A quick look at the Inspiron 700M owners manual on dell.com indicates that the maximum resolution of the LCD is 1280x800, not 1280x960...

--Gene

---

### Post by jenred on 2006-04-09
You need to install 855resolution -- there is an ubuntu package.  Follow the instructions in the readme.  1280x800 is the maximum resolution (as the previous poster pointed out.)

---

