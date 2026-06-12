---
title: "SiS &amp; direct rendering"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by Snakey on 2005-08-18
```
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M65 0/740 PCI/AGP VGA Display Adapter
```
When I type glxinfo | grep "direct", I get the following:
```
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

Does this videocard support direct rendering? And how do I enable it?

---

### Post by az on 2005-08-18
[http://ubuntuforums.org/showpost.php?p=305638&postcount=7](http://ubuntuforums.org/showpost.php?p=305638&postcount=7)

---

### Post by Snakey on 2005-08-18
[QUOTE=azz][http://ubuntuforums.org/showpost.php?p=305638&postcount=7](http://ubuntuforums.org/showpost.php?p=305638&postcount=7)[/QUOTE]
 This means it doesn't work with SiS 651?

---

### Post by az on 2005-08-18
"* DRI is only supported on the 300 series (300/305, 630, 730). A DRI driver for the SiS 300 series is provided by XFree86 4.1, 4.2(.1), XFree86 4.4 and X.org 6.7.0 and later. XFree86 4.3 does not contain a SiS DRI driver; However, installing the drivers from 4.2(.1) works well.
* Once again: There is no DRI/OpenGL/3D support for the SiS 6326, 5597/5598, 530/620, 315, 550, 650, 651, 740, 330, 661, 741, 760, 761 including all model variations with letters in the model number.
"


No.  Sorry.

---

### Post by Snakey on 2005-08-18
[QUOTE=azz]"* DRI is only supported on the 300 series (300/305, 630, 730). A DRI driver for the SiS 300 series is provided by XFree86 4.1, 4.2(.1), XFree86 4.4 and X.org 6.7.0 and later. XFree86 4.3 does not contain a SiS DRI driver; However, installing the drivers from 4.2(.1) works well.
* Once again: There is no DRI/OpenGL/3D support for the SiS 6326, 5597/5598, 530/620, 315, 550, 650, 651, 740, 330, 661, 741, 760, 761 including all model variations with letters in the model number.
"


No.  Sorry.[/QUOTE]
Then I'll buy a new graphic card  O:)

---

