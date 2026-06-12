---
title: "GRUB question"
date: 2008-10-09
forum: General Help
---

### Post by Skaarg on 2008-10-09
Currently I have a dual boot with XP and Ubuntu. Well I got a Vista Ultimate upgrade disc cheap from school, and I figured I'd give it a shot on my new computer since it didn't take too well on my old one.
Well obviously I don't what to screw things up so I can no longer boot to Ubuntu. Will using the Vista upgrade screw things up to where it only boots to Vista?

---

### Post by GreigKM on 2008-10-09
It will mess up the boot by fixing Windows MBR settings, But you can fix it through the Ubuntu live CD. There is a very good guide to it on the fourms: [How to restore Grub from a live Ubuntu cd]("http://http://ubuntuforums.org/showthread.php?t=224351") and with how much Windows needs to be re-installed, you'l use this alot!

---

### Post by mikewhatever on 2008-10-09
Yes, it most probably will. The good news is that if Ubuntu's partition stays intact, GRUB boot loader can be easily restored.
Super GRUB disk is one way of doing it.[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Skaarg on 2008-10-09
Thanks a lot, that's all I needed to know.

---

### Post by WWSmith36 on 2008-10-09
On a single hard drive system, Vista will overwrite grub and install its own bootloader.  After installing Vista, you can easily reinstall grub though.

Here is a link to a good community doc.  Steps 1-5 will reinstall grub. Step 6, is a manual edit of menu.lst to put Vista in your grub boot menu.  Just make sure you are using the proper partition in the root command.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

