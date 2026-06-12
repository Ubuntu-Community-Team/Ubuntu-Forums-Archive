---
title: "laptop 1366x768 Ubuntu 9.10 sis 672 driver"
date: 2009-11-11
forum: Hardware
---

### Post by osana412 on 2009-11-11
Any body have a solution for me? I have change xorg.conf using vesa, but only 1024x768 resolution I get (the picture not proportional). I have search at google and this forum, I have not found any solution.
I have try using sis671 but my screen chaotic.
I use dual system.
In Windows 7, looks better with resolution 1366x768.
But Ubuntu 9.10 only 1024x768.

Any help? Thnx b4.
:P

---

### Post by andydch on 2009-11-11
I have some info for you. Perhaps it can help.
These are some of content of my xorg.conf

```
Section "Device"
    Identifier     "Device0"
    Driver         "sis671" 
EndSection
```

try change sis671 with sis672 in your xorg.conf then restart
don't forget to install the driver...
if you dont have one, find it here
[http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=FrontPage]("http://ncc-1701a.homelinux.net/%7Elinux-sis/index.php?page=FrontPage")

good luck :popcorn:

---

### Post by osana412 on 2009-11-23
I have tried but can't... my screen blank. so I use backup again. What must I do? can u give a detail solution. Thnx for the answers.

---

### Post by purct on 2010-02-04
> **osana412 said:**
> I have tried but can't... my screen blank. so I use backup again. What must I do? can u give a detail solution. Thnx for the answers.

can you run:

sudo get-edid

and post the results?

---

### Post by bejostobbo on 2010-02-05
I found sis671 driver for Ubuntu 9.10
Res : 1280*800
Hope can help.
Download link :
[http://sharecash.org/download.php?file=366437](http://sharecash.org/download.php?file=366437)
or
[http://uploading.com/files/1cc9be67/xorg-driver-sisimedia_0.9-1_i386.deb/](http://uploading.com/files/1cc9be67/xorg-driver-sisimedia_0.9-1_i386.deb/)

---

### Post by purct on 2010-02-11
> **osana412 said:**
> Any body have a solution for me? I have change xorg.conf using vesa, but only 1024x768 resolution I get (the picture not proportional). I have search at google and this forum, I have not found any solution.
I have try using sis671 but my screen chaotic.
I use dual system.
In Windows 7, looks better with resolution 1366x768.
But Ubuntu 9.10 only 1024x768.

Any help? Thnx b4.
:P

What make of latop are you using?  what screen is it?

---

