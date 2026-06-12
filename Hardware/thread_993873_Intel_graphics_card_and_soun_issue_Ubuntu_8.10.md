---
title: "Intel graphics card and soun issue Ubuntu 8.10"
date: 2008-11-26
forum: Hardware
---

### Post by HishamN on 2008-11-26
Hi,

I have Fujitsu Siemens Amilo Pro V3205 with these cards:

1-  VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

2-   Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

It was working great on ubuntu hardy 8.041

Now I have Ubuntu 8.10 (Fresh installation) and these cards work but with some issues

Graphic card on Counter strike (Network game) make some fighters black!

Sound card has some noising sound on ubuntu startup and also on counter strike!

I want to increase Video shared memory to 128MB maybe it will solve graphic issue (I can't find Video shared memory in BIOS)

the output for dmesg is:

[   16.617737] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   16.618704] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   16.635974] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000

Is that mean that I only use 8MB for Video shared memory?

Thanks

Regards

---

