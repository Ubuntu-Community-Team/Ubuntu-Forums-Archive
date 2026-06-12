---
title: "fixing installation"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by yehudab on 2009-06-12
I'd be happy to get answer for my question. 
In my computer there are three hard-disks as the following: 2 disks have windows XP pro installation (Sys & Data)and the last one installed by Ubuntu 8.1. 
Some time ago, I re-installed windows on the original disk (not formatting), Ubuntu just disappeared. I mean, in - Storage management, I can see it and it divided into the right and original partitions, but I can't see it when I restart my computer. 
I tried to change the Order in the computer set-up, and I got an error message that it is not bootable disk.
It used to work, I don't know what happened.
Needless to note that at the win.ini, Ubuntu is not mentioned at all. 
Thanks in advance.
Yehuda

---

### Post by presence1960 on 2009-06-12
when you reinstalled windows you overwrote the GRUB bootloader. You need to restore GRUB by doing this :

```
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
```

If you are not sure what to do in steps 5 & 6- run in terminal ```
sudo fdisk -l
``` BTW that is a lowercase L. Post the output back here.

---

