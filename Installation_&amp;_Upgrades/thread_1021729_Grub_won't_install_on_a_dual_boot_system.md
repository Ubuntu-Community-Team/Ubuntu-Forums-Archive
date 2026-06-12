---
title: "Grub won't install on a dual boot system"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by The Anti-Conformist on 2008-12-25
I have 2 hard drives, one with windows xp on it, the other which i plan on having ubuntu 8.10 on it. The problem is that at the end of the installation the boot loader won't install. I've tried manually installing it in live cd, but it simply can't find the grub file. I've also tried searching in the drive, and i was able to find the grub folder with the stage1 file that I was trying to look for... I've also messed around with the area which the grub should be installed in the advanced button at step 7 of the installation process. None of these solutions that I saw worked for me. Is there another one?

---

### Post by hazeyfaze on 2008-12-25
Probably going to need a little more information to help... for instance, what is the error message occuring during the install process when the bootloader should be installing?  What is your partition layout for the Ubuntu installation?  What commands were you trying to install grub from the live cd?

Here are steps I usually follow:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2008-12-26
So what kind of error do you get during the boot loader part of the installation? Depending on the error you are getting, one thing you could try is to format the Ubuntu partition to ext2 instead of ext3 and try installing again; there is a known bug where the installer hangs when installing Grub and formatting to ext2 is a known workaround. If it works, you can easily "upgrade" the ext2 file system to ext3 afterwards, but let me know if that helps or not first.

---

