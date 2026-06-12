---
title: "menu.lst changed after update 8.10"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by Derko on 2009-04-16
After Ubuntu 8.10 did some updates my menu.lst has been changed and now I cannot boot into Ubuntu.
I know how to edit menu.lst by booting from the live CD but I do not know the syntax.
I tried this:

root (hd0,5)
kernel /vmlinuz root=/dev/sda6

but this results eventually in

...
...
...
[0.920183] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I hope this is trivial.

Derko

---

### Post by ajgreeny on 2009-04-16
Do you have any idea what changes were made?  Perhaps there is a backup of the original which you can use as a template for the new one.  I am surprised there is a problem, however, unless it's just a case of a new kernel which needs a graphics driver installed before you can get the GUI up and running.

What exactly are your symptoms?  I don't think a normal update would do anything unless a new kernel was installed, so the graphics driver is very likely.  Try starting in recovery mode and choosing xfix at the menu which appears.

---

### Post by muteXe on 2009-04-16
My update added a load of new kernel options to the list, but it was just a case and commenting out all the ones i dont want.  I normally just leave the latest kernel version, and its safe mode equivalent (and xp).

Not sure how it could screw anything major up.

---

### Post by Derko on 2009-04-16
It was just the automatic Ubuntu-update. I remember it asked something about the menu.lst and I think I chose something like "keep original menu.lst". Then it rebooted with above result.

Does anybody know how menu.lst can be rebuilt or editted by me because I think my Ubuntu-installation is OK but only my menu.lst is corrupt.

Derko

---

### Post by ajgreeny on 2009-04-16
If you run the Live Ubuntu CD and from that post the output of ```
sudo fdisk -l
``` and ```
sudo blkid
```  then mount the installed ubuntu partition and show us your current non-working /boot/grub/menu.lst, it should be possible to tell you what to change to get it working again.

---

### Post by Derko on 2009-04-16
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ab852fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       14593    76260555    5  Extended
/dev/sda5            5100        5585     3903763+  82  Linux swap / Solaris
/dev/sda6            5586       14593    72356728+  83  Linux
ubuntu@ubuntu:~$ sudo blkid
/dev/sda5: UUID="e2b2210d-b9b1-4afa-9c2f-6866dc571a48" TYPE="swap" 
/dev/sda6: UUID="2871f0e0-19e2-4ea7-8b8e-a42c84c6d224" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$

---

### Post by kvarley on 2009-04-16
My brother had exactly the same problem!

He managed to fix it using super grub disc.

gnu/linux > fix option

You can grab super grub disc here: [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Hope this helps.

---

### Post by ajgreeny on 2009-04-16
What about your current /boot/grub/menu.lst?  That would be very helpful as well.  I agree it's worth trying supergrub, which I tend to forget, never having needed to use it.

---

### Post by Derko on 2009-04-17
Sorry, forgot to include menu.lst
Now i'm at work. Will do it this evening.

But maybe you can explain the menu.lst syntax

root (hd0,5)
kernel .....

What comes after 'kernel'. As I remember something with this UUID-code ?

Derko

---

### Post by ajgreeny on 2009-04-17
OK, here's a template from (8.04) to give you a clue.

```
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=6338bfe4-eb42-4fd9-a621-2320b27884f5 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet
```

---

