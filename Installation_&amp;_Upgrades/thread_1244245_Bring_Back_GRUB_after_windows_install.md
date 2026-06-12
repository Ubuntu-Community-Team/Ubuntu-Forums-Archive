---
title: "Bring Back GRUB after windows install"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by petrospet on 2009-08-19
Hello! So here is the problem. I have a dual boot vista-ubuntu 9.04 on my vaio and everything was great.Then I decided to replace vista with the windows 7 RC. I installed it over the windoze partition of course leaving my ubuntu partitioned unharmed. Of course now I have no bootloading options. So how do I bring back the GRUB or any kind of bootloading options so I can access my favourite OS again??

---

### Post by drs305 on 2009-08-19
Here is a common link for restoring grub after installing Windows. I don't know if the procedure changes for RC7:
[RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

---

### Post by presence1960 on 2009-08-19
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In #6 use setup (hdx) where x is the number of your hard disk. remember numbering starts at 0. so the first hard disk (sda) would be (hd0), the second hard disk (sdb) would be (hd1). You want to put GRUB on MBR of the first boot disk so it will take over instead of windows bootloader.

---

