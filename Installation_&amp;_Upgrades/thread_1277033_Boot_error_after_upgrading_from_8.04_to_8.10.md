---
title: "Boot error after upgrading from 8.04 to 8.10"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by Terraman on 2009-09-27
Dear Ubuntu Friends,

I've just upgraded my elderly notebook from 8.04 to 8.10 and come up with this error in boot sequence:

```

Starting up...
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args(cat /proc/cmdline)
  -check root delay= (did the system wait long enough?)
  -check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules;ls /dev)
Alert! /dev/disk/by-uuid/1bd1dd50-835b-4cf6-b590-dbff4c83d446 does not exist Dropping to shell!

BusyBox v1.10.2. (Ubuntu 1:1.10.2-1ununtu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

Can anyone help me?

Thanks in advance!

---

### Post by pedja_portugalac on 2009-09-27
Thats why I like to install fresh and not to upgrade.
Try to reboot ones again.

---

### Post by lswb on 2009-09-27
From the error messages you've posted I would say that the actual UUID of your root partition is not what is being used in /boot/grub/menu.lst. Boot from a live CD and open a terminal. Mount the hard disk rw if necessary, I don't remember if the live CD automatically does that or not. Open a terminal and use the command "blkid" to find the uuid of the partitions on your hard drive. Then use gedit or other editor to open the menu.lst file on the hard drive. You should find some lines looking something like this:

```

title           Ubuntu 9.04, kernel 2.6.31-020631-generic
uuid            41209907-0c68-4c13-9a5f-fe693514fce3
kernel          /boot/vmlinuz-2.6.31-020631-generic root=UUID=41209907-0c68-4c13-9a5f-fe693514fce3 ro 
initrd          /boot/initrd.img-2.6.31-020631-generic
quiet

title           Ubuntu 9.04, kernel 2.6.31-020631-generic (recovery mode)
uuid            41209907-0c68-4c13-9a5f-fe693514fce3
kernel          /boot/vmlinuz-2.6.31-020631-generic root=UUID=41209907-0c68-4c13-9a5f-fe693514fce3 ro  single
initrd          /boot/initrd.img-2.6.31-020631-generic

```
substitute the actual uuid of your root partition where the long string beginning with "41209..." is shown in the example here. On your system, you will probably see the uuid "1bd1dd50..." that was in the error message you posted.

While you are in the live CD environment, if you have big enough usb drive or external drive of some kind, save any important files or data from the hard drive. It is possible there are other problems with the upgrade, and with your data saved off disk, you can do a clean install if necessary.

---

### Post by Terraman on 2009-09-28
> **pedja_portugalac said:**
> Thats why I like to install fresh and not to upgrade.
Try to reboot ones again.

Yes, maybe you're right, but I'm playing with it and trying to learn how Linux works.

Thank you very much.

---

