---
title: "USB root filesystem unmounts"
date: 2009-06-26
forum: Hardware
---

### Post by kartik_vad on 2009-06-26
Motherboard: Asus A8v-MX.

My root filesystem is on a USB drive (since Ubuntu doesn't support my SATA internal hard disc). More precisely, it's a USB enclosure into which I put my SATA disc. After a few hours of use, the machine sometimes crashes because the root filesystem becomes unmounted -- doing an ls in /dev does not list the volume. When this happens, fonts in dialog boxes show only square boxes for all characters, presumably because the font cannot be loaded/mmapped in.

When this happens, I've found that power-cycling the machine doesn't necessarily help; I sometimes have to power-cycle the USB enclosure. Which leads me to believe the problem is with the USB enclosure rather than with Linux hardware support for USB on my motherboard.

Should I
a) buy a new USB enclosure?
b) buy a PATA disc?
c) buy a whole new computer?

Is there any way to determine from the logs if the USB device has malfunctioned, in which case a new USB enclosure presumably helps, or if it's an issue on the Linux side of things? Or should I just go buy a PATA disc?

I've tried connecting this disc to my macbook; I'll see if it suffers unmounts there. Any advice is greatly appreciated. Thanks!

---

