---
title: "A different kind of HP PSC problem"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by fisaacs on 2005-03-12
Ok, so I've got a PSC 1210 and went through the usual gnome add-printer option, as well as the installation of the hpoj package from universe or multiverse or wherever its usually kept.

Printing was going fine before I installed hpoj, scanning wasn't  :( 

Scanning now works fine, but printing doesn't.   :evil: 

When I try to print, the printer queue automatically pauses itself.  on trying to un-pause it, it waits a few seconds and pauses itself again.  In addition, I noticed that whatever's going on is affecting the rest of my computer because the sound-processing in rhythmbox starts sounding real nasty .  :-k 

Insofar as other possibly relevant hardware goes: P4 2.6 Hyperthreading, motherboard has Intel i865PE chipset, i810 audio.  

I suspect this is an odd interaction with the usb kernel modules specifically used in SMP kernels because I'm also running that, and hpoj gave me an interesting warning about it.

---

