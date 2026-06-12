---
title: "ubuntu hardy won't recognize my windows xp tiny"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by levente88 on 2008-12-23
hey everyone.
i downloaded a windows xp tiny("platinum edition") to completely reconfigure my home computer
instalation went perfect but afterwards when i instaled ubuntu hardy over it, i got a glitch :|
when i boot up and i get to select the os i want to boot, i can't find the windows os. any feedback on how to fix it would be gr8.
thanx in advance.

---

### Post by taurus on 2008-12-23
You said you reinstalled Ubuntu over it, does it mean you wiped out your widows when you installed Ubuntu?

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by levente88 on 2008-12-23
i specially partitioned the disc when installing windows and when installing ubuntu i just fitted them into place as root, home, swap, and windows. the windows partition is still there and i can acces it through ubuntu, i just can't get it to boot up.this doesn't usually happon with a genuine windows. but since this one has been tampered with it could explain things

here's what you asked:
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dc92dc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381   83  Linux
/dev/sda2            1306       10010    69922912+   f  W95 Ext'd (LBA)
/dev/sda5            1306        1566     2096451   82  Linux swap / Solaris
/dev/sda6            1567        3524    15727603+   7  HPFS/NTFS
/dev/sda7            3525       10010    52098763+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa961859c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)

i also have a 500GB external hard drive, hence the result. but it just contains the backed up data until i can get the os right on the computer

---

### Post by taurus on 2008-12-23
> /dev/sda6 1567 3524 15727603+ 7 HPFS/NTFS

I don't think windows is too happy to be in a logical partition.  It needs to be a primary so that could explain why it wouldn't boot.

Look in /boot/grub/menu.lst to see if there is an entry for windows.

```
cat /boot/grub/menu.lst
```

---

### Post by levente88 on 2008-12-23
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=8bc01b5e-3d92-4d6b-88e2-85aee2c40c85 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=8bc01b5e-3d92-4d6b-88e2-85aee2c40c85 ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8bc01b5e-3d92-4d6b-88e2-85aee2c40c85 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8bc01b5e-3d92-4d6b-88e2-85aee2c40c85 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
 
not even the slightest sign of windows. the thing is it booted up just fine before instaling ubuntu. i had it allready configured since i thought that would be the motherload of the entire process

---

