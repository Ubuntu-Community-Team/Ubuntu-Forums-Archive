---
title: "TV out on Breezy + Amilo Pro"
date: 2006-05-04
forum: Hardware &amp; Laptops
---

### Post by Hellkeepa on 2006-05-04
HELLo!

I was wondering if anyone here could help me with getting the TV out on my laptop to work? I've tried searching both here and google, but I can only find vague referances or howtos for entierly different setups.

Happy tinkerin'!

---

### Post by JKoder on 2006-05-05
Hi
First of all let us know what video card do you have ? Perhaps VIA S3 Unichrome Pro ???

---

### Post by Hellkeepa on 2006-05-05
HELLo!

Ah, sorry about that little slip of my mind.
Unfortunately I don't have that chipset, as I lifted this from xorg.conf:
```
Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection
```
So it seems I have an Intel i810 chipset.

Happy codin'!

---

### Post by Hellkeepa on 2006-05-05
HELLo!

Just tried this one, and it seemed to work. Haven't tried it out though, but I'll let you know how it works.

[http://ubuntuforums.org/showthread.php?t=141031&highlight=i810+tv](http://ubuntuforums.org/showthread.php?t=141031&highlight=i810+tv)

Happy codin'!

---

