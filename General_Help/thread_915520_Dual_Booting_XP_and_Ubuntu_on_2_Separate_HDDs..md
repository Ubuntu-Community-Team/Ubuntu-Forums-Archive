---
title: "Dual Booting XP and Ubuntu on 2 Separate HDDs."
date: 2008-09-09
forum: General Help
---

### Post by RtoddDillon on 2008-09-09
I tried reading the older posts, but I can't seem to figure out my problem...  I have a machine which was already running Hardy on a SATA and decided to install XP to my IDE drive so I could play Spore.  Well after installing XP to the IDE drive I cant get Linux to load... even after removing the HDD containing XP from the boot sequence options.  When I do that my computer tells me that I need to install a directory to load my operating system- like it doesnt recognize the other HDD (SATA) installed in the computer.

Again, sorry if this has been tackled before, I looked but couldn't find and I'm new to the boards

---

### Post by fooman on 2008-09-09
the windows bootloader has overwritten the mbr. you need to reinstall grub.  this should help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by RtoddDillon on 2008-09-10
Thanks, I really appreciate it,  I'll try it right away

---

### Post by RtoddDillon on 2008-09-10
Hey, that worked to bring up  grub but after that when I tried to boot back into Ubuntu it said "Error 15" file not found...

---

### Post by joshuachad on 2008-09-10
Make sure that grub is pointing to the right partition that contains your kernel for example in mine the section that starts with root (hd0,2)
point to /dev/sda3. I would dig deeper in that tutorial he gave you. Its not finding your kernel image.

---

