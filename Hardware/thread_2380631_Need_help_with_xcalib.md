---
title: "Need help with xcalib"
date: 2017-12-19
forum: Hardware
---

### Post by uwe-bungto on 2017-12-19
I have a dual monitor setup with a Nvidia K 4000 graphic card
Finally managed to make 2 profiles one for each screen.  
using dispcal, targen, dispread and colprof.
The profiles are
screen 1 : DP2.icc
screen 2 : DP3.icc
after the display port numbers

What is the naming convention for screens in xcalib
xcalib  -d :0 -s 0 .local/share/color/icc/Dell-DP2.icc
install on screen 0 DP2

xcalib  -d :0 -s 1 .local/share/color/icc/Dell-DP3.icc
Gives a warning
```
X Error of failed request:  BadValue (integer parameter out of range for operation)  Major opcode of failed request:  151 (XFree86-VidModeExtension)
  Minor opcode of failed request:  19 (XF86VidModeGetGammaRampSize)
  Value in failed request:  0x17
  Serial number of failed request:  10
  Current serial number in output stream:  10
```

Where am I going wrong??

---

