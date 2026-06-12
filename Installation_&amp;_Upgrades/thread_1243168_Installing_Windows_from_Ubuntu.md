---
title: "Installing Windows from Ubuntu"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by screeming mantis on 2009-08-18
Alright, long story short my computer stopped working after a botched windows 7 install and I had to save the poor thing using ubuntu since it's a live installer and I could boot it from the BIOS. Now I want to re-install Windows on my hard drive. Just Windows. I do NOT want to dualboot, or use an emulator. However, whenever I go to re-install 7 using wine it'll give me an insufficient memory to copy temp. files. How do I go back to using Windows? Apologies if this is extremely obvious, I *just* installed Ubuntu a few hours ago.

---

### Post by Katalog on 2009-08-18
Can't you just boot from the Windows 7 CD by setting the boot order in the BIOS to boot from the CD drive first?

---

### Post by screeming mantis on 2009-08-18
> **Katalog said:**
> Can't you just boot from the Windows 7 CD by setting the boot order in the BIOS to boot from the CD drive first?
 I tried. It'll attempt to boot, and then just load Ubuntu. it seems as if you need to be running an OS to use the CD
edit: I also did the same thing with a Windows XP disk and got the same result.

---

### Post by dandnsmith on 2009-08-18
You're not, on that evidence, set to boot from anything before the HDD.
You need to look into the BIOS settings, and (probably) change the order of boot so that CD comes before HDD.

---

