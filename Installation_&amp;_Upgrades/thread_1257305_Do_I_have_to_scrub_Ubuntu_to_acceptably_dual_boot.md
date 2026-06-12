---
title: "Do I have to scrub Ubuntu to acceptably dual boot"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by oake on 2009-09-03
Hi
I am trying to dual boot my machine starting from an up to date Ubuntu install. I want to end up with XP running from a c:\, but following apcmag** and on route there's a paragraph (below), found it result in an f:\   

 I guess, unless there is a partition editor trick? so XP installs onto what it thinks is a c: drive, I'll be scrubbing the whole disk.
 Thanks for your consideration
 

**[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm#](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm#)
 ...
 For the operating system and the vast majority of Windows applications which have properly-coded installation scripts, this is not a problem. Some older applications will assume that C: is the system partition and may bring up errors. There are ways of changing the drive letter assignation of the system partition, but in this scenario it's strongly discouraged.
 ...

---

### Post by fatbotgw on 2009-09-03
I believe you can use gParted (from a live disk) to move the ubuntu partition to the "end" of the drive so that all of the free space shows up to the left (in gparted) of the linux install.  You should then be able to install Windows into the free space at the "beginning" of the drive...which is what Windows likes.

It should be the "resize/move..." option

---

### Post by oldos2er on 2009-09-03
The usual advice given here on the forums is the opposite of what that article says; i.e. you would install Windows first, then Ubuntu. FWIW.

---

