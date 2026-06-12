---
title: "Beryl, Legacy nVidia, Riva TNT2 - Impossible?"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by allwin on 2007-01-06
I have an old test box here with an nVidia Riva TNT2 16Meg card with TV out.  If I use the ENVY script, it downloads the 7184 LEGACY nVidia driver and uninstalls nvidia-glx-legacy package.  If I install the nvidia-glx-legacy package, that uninstalls the 7184 driver and forces me to use the nv driver which has no accel.

Seems like I'm at a catch-22.  Is it even possible to get Beryl running with such an old video card?  With nvidia-glx-legacy installed, I can't get the 7184 driver to work (X crashes).  With the 7184 driver installed via ENVY, there's no GLX and Beryl dumps.

I've tried a zillion things, enabling COMPOSITE, disabling it, loading DRI, not loading DRI, out the wazoo.  Should I give up?

---

### Post by energiya on 2007-01-07
Read [this]("http://ubuntuforums.org/showthread.php?t=319844"). I have a 32MB RIVA TNT2 M64 Pro and doesn't work...

---

### Post by allwin on 2007-01-14
Follow up!  I found an ATI Radeon 7000 32M AGP graphics card on Ebay for $15.  Slapped it in my old 1999-era box and using the ATI driver (open source one) I got Beryl to work (0.1.4) under AIGLX.  Might be a solution for those of you out there looking to escape the nVidia world.

ONLY TROUBLE IS...SCROLLING IN FIREFOX, ETC, IS SLOWWWWWWWWWWWWWWWW!

Seems to be a driver issue.  If only you could find ONE combination of stuff that worked completely in this Ubuntu universe!

---

### Post by nibsa1242 on 2007-01-14
While I'm running on more modern hardware then you are Beryl + Firefox is an unstable combo on my machine. I'm glad it works even slowly for you. Beryl seems fine with everything else, but with firefox something as simple as having two firefox windows on different workspaces can cause a hard lock, or opening something in a new window.  If it seems somewhat stable then I'd be happy.

---

