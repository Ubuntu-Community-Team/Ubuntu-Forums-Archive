---
title: "Monitor &amp; Mounting trouble"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by Kmujo on 2007-04-30
Ok so i decided to give feisty fawn a run over my previous openSUSE 10.2 experience. thus far, i'm not liking alot of things, but besides that. I'm currently having difficulties getting dual-head display to work and correct my monitor resolution(s);usually in SUSE/YaST2 i can choose my monitor type and what not, but i see no such thing in ubuntu that i can change my monitor to use the correct driver. i tried manually configuring the xorg.conf to use the Dell P991 specs, but my screen just stays blank and what not. so if anyone have an idea how to fix this, it'll be much appreciated. 

Secondly, i have several other hard drives that i'll like accessible to other users on the desktop, but there's no mount utility in ubuntu that i can use to setup them up. i'm not familiar with my hard drive parameters, so i havent tried manually configuring them in fstab.

Oh, i'll also like to know how can i enable dual-head display on my nvidia device. in the xorg.conf, somethings are currently reading wrong. like the type of card i have (NV 6800XT) instead, reading as a 6600 GS.

---

### Post by veloce on 2007-04-30
> **Kmujo said:**
> Ok so i decided to give feisty fawn a run over my previous openSUSE 10.2 experience. thus far, i'm not liking alot of things, but besides that. I'm currently having difficulties getting dual-head display to work and correct my monitor resolution(s);usually in SUSE/YaST2 i can choose my monitor type and what not, but i see no such thing in ubuntu that i can change my monitor to use the correct driver. i tried manually configuring the xorg.conf to use the Dell P991 specs, but my screen just stays blank and what not. so if anyone have an idea how to fix this, it'll be much appreciated. 

Secondly, i have several other hard drives that i'll like accessible to other users on the desktop, but there's no mount utility in ubuntu that i can use to setup them up. i'm not familiar with my hard drive parameters, so i havent tried manually configuring them in fstab.

Oh, i'll also like to know how can i enable dual-head display on my nvidia device. in the xorg.conf, somethings are currently reading wrong. like the type of card i have (NV 6800XT) instead, reading as a 6600 GS.

There is a howto on setting up your xorg.conf for dual head (search for the "xinerama" thread)

---

