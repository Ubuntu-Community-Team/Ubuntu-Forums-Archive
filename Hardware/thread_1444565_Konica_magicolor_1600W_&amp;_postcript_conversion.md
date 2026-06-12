---
title: "Konica magicolor 1600W &amp; postcript conversion"
date: 2010-04-01
forum: Hardware
---

### Post by gdcondor on 2010-04-01
Hello,

I've a new printer Konica magicolor 1600W which was recognized out of the box with the driver foo2lava
But it doesn't work while printing pdf or other files from evince (or some other softwares), I think because Evince doesn't convert my pdf files to postscript ?

If I do it manually it works after printing my file to .ps with evince and :
```
foo2lava-wrapper -z2 -c -C2 -r1200x600 -p26 -m0 -s255 -d1 -Gkm-1600-rgb-392-bpp1.icm file.ps > xxx.prn
sudo cp xxx.prn /dev/usb/lp0
```
Is there something to install with cups or some config trick ?

Thanks for your help !

Florian

---

