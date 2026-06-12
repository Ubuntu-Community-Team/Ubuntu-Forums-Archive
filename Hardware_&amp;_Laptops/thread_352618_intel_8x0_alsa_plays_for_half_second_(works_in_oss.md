---
title: "intel 8x0 alsa plays for half second (works in oss)"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by senebirt on 2007-02-03
Sound card is 82801FB ICH6 (according to lspci and alsaconf); alsamixer shows ICH6 Chip: AF1981B
I tried all the different versions of alsa-driver with no luck (
even 1.0.14rc2).  i810_audio works for OSS.  snd-intel8x0 is the module for ALSA if that helps anything..

I am attempted updating the kernel but that didn't even boot all the way and detected the same chip during the boot up process.  

I played around with alsamixer and /etc/init.d/alsasound but nothing worked.

I need alsa to work in order to use flash9, none of the OSS work arounds work for this.  

Maybe this is a bug with Alsa? 

I am new to Ubuntu (not linux).  Any help would be greatly appreciated.. Thanks..

---

### Post by senebirt on 2007-02-05
fixed problem.  added pci=noacpi to kernel boot line if anyone has this problem in the future attempt this.

---

