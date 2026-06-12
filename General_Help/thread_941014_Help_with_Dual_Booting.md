---
title: "Help with Dual Booting?"
date: 2008-10-07
forum: General Help
---

### Post by Alienwarek on 2008-10-07
Ok so heres whats wrong: I installed Ubuntu on my lapop then a month or so later I installed Win Xp after I did that only XP would boot (and it wouldn't ask what I wanted to boot) so someone told me that I needed to reinstall the GRUB loader so I did and now only Ubuntu will boot (and again it wouldn't ask what I wanted to boot)... Can someone help me?

---

### Post by RATM_Owns on 2008-10-07
Could you post the outputs of
```
sudo fdisk -l
```

And what's inside your /boot/grub/menu.lst?
```
gedit /boot/grub/menu.lst
```

---

### Post by MasterNetra on 2008-10-07
Thats the problem you installed ubuntu first. Your suppose to install windows first. Because windows overrides grub when installed. You will have to re-install grub. I would recommend using Super Grub for that. Otherwise your next option is re-installation of Ubuntu.

---

### Post by Alienwarek on 2008-10-07
sudo fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5c8be18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7295    58597056   83  Linux
/dev/sda2            7296        7357      498015   82  Linux swap / Solaris
/dev/sda3   *        7358       14592    58115137+   7  HPFS/NTFS
---------------------------------------------

gedit /boot/grub/menu.lst:

default 0
timeout 3
hiddenmenu

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=432837f7-6bea-45f9-b0eb-8b12f6de1b88 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=432837f7-6bea-45f9-b0eb-8b12f6de1b88 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=432837f7-6bea-45f9-b0eb-8b12f6de1b88 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=432837f7-6bea-45f9-b0eb-8b12f6de1b88 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

---

### Post by caljohnsmith on 2008-10-07
OK, open up your menu.lst again:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following at the end:
```
title  Windows XP
root (hd0,2)
chainloader +1
```
Also, really important, make sure you put a pound sign # in front of the line that says "hiddenmenu" so it looks like:
```
#hiddenmenu
```
Save, quit gedit, reboot, and you should see the Grub menu now and be able to choose Windows. Unless there are other issues with Windows, that should be all it takes to boot Windows. Let me know how it goes.

---

### Post by mosflm on 2008-10-08
I am posting it here, because I can't somehow start a new thread on this forum. I have a problem with dual boot. I would be very greateful if you could help! 

I have ubuntu 8.04 installed. I boot from live CD - shrink the partition to half hard drive size, leaving unpartitioned space for windows. Reboot and boot from windows XP installation CD, but it says it can't detect any harddrive mounted. 

I know it's better to have windows first. But now if I erase all ubuntu partitions with GParted, it makes no difference - windows still can't detect any harddrive, while under ubuntu evrth works just fine.

How can I solve this?

---

### Post by mosflm on 2008-10-08
> **caljohnsmith said:**
> OK, open up your menu.lst again:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following at the end:
```
title  Windows XP
root (hd0,2)
chainloader +1
```
Also, really important, make sure you put a pound sign # in front of the line that says "hiddenmenu" so it looks like:
```
#hiddenmenu
```
Save, quit gedit, reboot, and you should see the Grub menu now and be able to choose Windows. Unless there are other issues with Windows, that should be all it takes to boot Windows. Let me know how it goes.

I am posting it here, because I can't somehow start a new thread on this forum. I have a problem with dual boot. I would be very greateful if you could help!

I have ubuntu 8.04 installed. I boot from live CD - shrink the partition to half hard drive size, leaving unpartitioned space for windows. Reboot and boot from windows XP installation CD, but it says it can't detect any harddrive mounted.

I know it's better to have windows first. But now if I erase all ubuntu partitions with GParted, it makes no difference - windows still can't detect any harddrive, while under ubuntu evrth works just fine.

How can I solve this?

---

### Post by caljohnsmith on 2008-10-08
Mosflm, I've seen a number of cases where the Windows Install CD doesn't recognize the Windows installation on a HDD when the HDD's partition table somehow got corrupted; that might be your case. How about first posting:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by Alienwarek on 2008-10-08
caljohnsmith Thx....

---

