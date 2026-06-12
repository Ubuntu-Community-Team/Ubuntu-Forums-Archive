---
title: "Windows Bootloader Only"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by Benz0r on 2009-08-22
Hello. Right now I'm wanting to install Ubuntu on a second partition. On the first I have Windows 7 installed. The thing is, I don't want to have GRUB boot loader. Last time I installed Ubuntu, it only showed Ubuntu, and I couldn't get back into Windows 7. Is there a way to not install the GRUB boot loader, or remove it so the Windows boot loader will be in charge?

Thanks, Benny.

---

### Post by wojox on 2009-08-22
Don't use Windows but I have seen this question come up before. People talk about EasyBCD. You may want to goggle and check it out. Hope that helps.

---

### Post by Benz0r on 2009-08-22
But if I install Ubuntu it will exclude the Windows boot loader. I wouldn't be able to go back in unless I edit stuff.

---

### Post by Arand on 2009-08-22
In the last screen (review of changes) you can look into advanced settings and there choose to "install grub" to the bootrecord of the ubuntu partition rather than the masterbootrecord (mbr).
Then you'll have to configure BCD to be able to chainload grub, Easiest way to do that is using EasyBCD.
But you could also make a copy of the grub-br and plug it into BCD using the preinstalled windows BCDedit tool <- this option will make you feel more h4xx0r.
- Arand

---

### Post by Mark Phelps on 2009-08-23
For assistance in using EasyBCD, go to the NeoSmart forums.  They have forums and how-to's that deal with what you're trying to do.

---

