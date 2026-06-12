---
title: "Creating a partition for windows while installing ubuntu"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by webster5 on 2009-08-09
I'm trying to install windows xp on a computer that has fedora installed right now. I ran into a few problems during that process. 
 
I have an ubuntu cd that I'm now trying to use to delete the partitions for fedora and to create a partition that can install windows xp. I have backed up the data from fedora and I'm switching to ubuntu. 
 
My plan is to create a partition for windows xp and then to create a few partitions for ubuntu. But the ubuntu cd doesn't allow me to set the windows xp partition as ntfs. It only offers options for fat 16/32.

Is there a way around this? There's also a "do not use this partition" option. Should I just create a partition using that option and then create partitions for ubuntu? Will the xp cd recognize and install on that partition? Thanks.

---

### Post by merlinus on 2009-08-09
You can format it as fat32, and xp should find it.  You might then be able to select ntfs, or you can change the format later on from windows without losing data.

---

### Post by presence1960 on 2009-08-09
use [gparted Live CD]("http://gparted.sourceforge.net/livecd.php") - you will be able to create NTFS partition as well as partitions for Ubuntu. Gparted Live CD is the more current than the gparted on the Ubuntu Live CD. When partitioning is done use the Windows install CD/DVD to install windows, then the Ubuntu Live Cd to install Ubuntu. If you install Ubuntu first you will have to restore GRUB after installing windows like this:
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

In #6 use setup (hd0) to install GRUB to MBR if you have a single hard disk.

---

