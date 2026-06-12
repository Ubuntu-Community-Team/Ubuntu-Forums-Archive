---
title: "Manually Updating GRUB?"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by zak89 on 2009-05-25
I would really like to try out the latest Moblin release on my MSI Wind. However, I am currently running Ubuntu Jaunty (NBR), 64Studio (based on Ubuntu Hardy) and Windows XP on this device, and the Moblin installer only recognizes Windows. I really want my Ubuntu Jaunty install to handle the bootloader, but once I install moblin, I can't even boot Jaunty.

I would like to have Jaunty reinstall GRUB and go from there; barring that, I would need to manually add entries to Moblin's GRUB menu for the other OSs. But I would want those entries to link to my other OS's *own* GRUB menus, to take care of kernel updates (I am testing the array.org kernels on my NBR install) and such.

So my first question; how can I get to my Jaunty install after installing Moblin and reinstall GRUB to the MBR? and, if not that, how do I add entries to GRUB for "third party" GRUB menus?

Thanks!

---

### Post by presence1960 on 2009-05-25
when all 3 OS are installed boot from the Ubuntu Live CD & choose "try Ubuntu without any changes to your computer". When the Desktop is ready open a terminal to restore GRUB:

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

In step #6 I would install GRUB to MBR.

I would suggest chainloading the other OS's. here is a clip from my menu.lst. I have Jaunty, hardy & XP. Hardy is chainloaded on Jaunty's menu.lst which is on MBR

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro quiet splash vga=789 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro quiet splash vga=789 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8319981e-03bb-4bd9-9d2e-276da66b4f1c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8319981e-03bb-4bd9-9d2e-276da66b4f1c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title           Ubuntu Hardy 8.04
rootnoverify    (hd1,1)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1

```

This will allow for kernel upgrades without editing menu.lst(s).

---

### Post by zak89 on 2009-05-25
Thanks! That looks like just what I was looking for!

If all goes well I'll be posting some crude "benchmarks" comparing NBR and Moblin, particularly with battery performance.

---

