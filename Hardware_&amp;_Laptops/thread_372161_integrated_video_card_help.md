---
title: "integrated video card help"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by redDEADresolve on 2007-02-27
I have a Dell Inspiron 1501 laptop with the ATI X1150 integrated video card. I'm running Ubuntu 6.10 Edgy Eft, have the proprietary ATI driver installed, have 1.5GB of memory.

I was wondering how I find out how much of my system memory is being used for the video card? How to enlarge or shrink it? Thanks for the help.

---

### Post by psyke83 on 2007-02-27
I don't have an ATI card, but there's a good chance that you can change it by editing xorg.conf and in 'Section "Device"' add:

        ```
VideoRAM        32768
```
 
Here's mine, for example:

```
Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID          "PCI:0:2:0"
        VideoRAM        32768
EndSection
```

Modify the value to anything you like, 32mb is just an example. As for finding the current setting, try checking the output of:

```
cat /var/log/Xorg.0.log | grep VideoRAM
```

---

### Post by redDEADresolve on 2007-03-02
Not working for me, this is what I get in my xorg,

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver      "ati"
	BusID       "PCI:1:5:0"

anyone else?

---

