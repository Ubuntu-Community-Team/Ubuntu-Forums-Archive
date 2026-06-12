---
title: "[SOLVED] Another &amp;quot;Had to reinstall XP&amp;quot; thread"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by gruss on 2008-12-20
Had my lattitude d630 dual booting 8.04 and XP, well XP became riddled with viruses and I had to reinstall fast since I need it for work.  Got some free time now and I'm trying to get back to ubuntu, so I thought I'd try GAG for a boot loader just for fun, but it would not boot Ubuntu on my pc...a google search turned up a lot of hits so I unistalled and just went back to grub following these instructions: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Grub is back and looks just like how I left it, but now I get an _**Error 17**_ Unable to mount volume when I try to boot ubuntu?  WinXP still boots fine from the grub selector.  I'm really hoping this is something silly I forgot/don't know.  Any help appreciated!

---

### Post by logos34 on 2008-12-20
try the suggestions 

[here]("http://users.bigpond.net.au/hermanzone/p15.htm#17")

(->'GRUB Command Line Interface method')

maybe menu.lst 'root' line needs editing

running fsck on ubuntu / from the live cd wouldn't hurt either

---

### Post by gruss on 2008-12-20
Thanks that link was extremely helpful, didnt stumble on it before.  fsack didnt do it just had to edit the menu.lst file, up and running again.

---

### Post by logos34 on 2008-12-20
ok, happy it's fixed.  Mark as 'Solved' (>Thread Tools) and enjoy!

---

