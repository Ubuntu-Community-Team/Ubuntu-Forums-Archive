---
title: "Ubuntu Installation on windows"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by bargi on 2009-08-09
Hi,
I am going to install ubuntu 8 on my system. I have already windows on my system. 

The fact I know is that if I installed ubuntu over windows then both  OS will be accessible. But if after installing ubuntu I I install windows ( due to corruption or some other purpose ) then Ubuntu will be not accessible.

Can any body help me, how to install ubuntu in such a way so that in future if I need to install windows there is no problem with ubuntu.

Can any body tell me the process. It will be helpful if specified in steps ( as I to follow them and while installing I can't access net).

Thanks

---

### Post by rogueleader12345 on 2009-08-09
The easiest way to do that is to put Ubuntu on another hard drive. I'm not sure if you partition your hard drive into, say, three partitions, if you can tell Windows which partition to install on. If so, that'd be the way to go. But it's been so long since I actually installed a version of Windows that I honestly don't remember if you can specify a partition.

---

### Post by presence1960 on 2009-08-09
it is not as bad as you think. If you install windows after Ubuntu (on the same hard disk) Windows bootloader overwrites GRUB on the MBR of the hard disk. All you need to do to restore GRUB is this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", or whatver your hard disk is to install GRUB to MBR.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

If you have a windows retail or OEM CD/DVD you can choose which partition to install Windows onto, as well as delete & create partitions from the installer. If you have a recovery CD/DVD you can't choose.

---

