---
title: "Jaunty &amp; video card"
date: 2009-08-11
forum: Hardware
---

### Post by dulac on 2009-08-11
hey, new Ubuntu user. I am having problems, please either point me to the right spot or lemme know of information...

I have a Desktop. Its two hard drive(one is Ubuntu 9.04 the other is Vista). I am running a Radeon HD 4670 graphics card( PCI/dual DVI) with 2 ACER monitors(DVI for both) ...

This happens:
   -Boot up with both monitors plugged in. 
   -when full boot is complete, One screen is jumpy and the other is fine, also, everything is slow.

When only 1 monitor plugged in:
   - No problems.

Is this my Graphics card? and is there a way to find out about good graphics cards compatible with Linux Ubuntu and dual dvi?

Any help is great, Thanks.

---

### Post by Vakman on 2009-08-11
Dual monitors can sometimes be hard to setup. First of all, have you installed your drivers? Post the output of
```
glxinfo | grep direct
```

---

### Post by dulac on 2009-08-11
i installed the FLX something driver that it told me to instal for my graphics card. ill post the input in about 20 mins when i get home.

---

### Post by dulac on 2009-08-11
the output is:

    direct rendering: Yes

now what??? Thanks.

---

### Post by Vakman on 2009-08-12
Follow this [HowTo]("http://ubuntuforums.org/showthread.php?t=983781&highlight=dual+monitor+howto+ati").
There might be a way to simply enable from the Catalyst Control Center now but whatever works.

---

### Post by Yellow Pasque on 2009-08-12
If you're trying to run a "big desktop" (not cloned), make sure you have the following in your device section:
```
Option      "EnableRandR12" "false"
Option      "DesktopSetup" "horizontal"
```

---

### Post by Vakman on 2009-08-14
> **Temüjin said:**
> If you're trying to run a "big desktop" (not cloned), make sure you have the following in your device section:
```
Option      "EnableRandR12" "false"
Option      "DesktopSetup" "horizontal"
```

Outlined in the HowTo, but not the "EnableRandR12" "false" line. What will that line do?

---

### Post by Yellow Pasque on 2009-08-14
Catalyst has some support for the X RandR, but the last time I checked, it was buggy, and that line was a necessary workaround for extending a desktop across multiple monitors.

---

