---
title: "[SOLVED] GRUB boots ubuntu partition instead of windows xp"
date: 2008-08-21
forum: General Help
---

### Post by CowboyFunk on 2008-08-21
So I installed windows xp after ubuntu, then I recovered grub using the live cd. Now in grub when I highlight windows xp to boot it up it boots up ubuntu instead of windows xp. I honestly can't think of what is wrong even after searching the internet many times.

here is my grub

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9b5b2512-01ad-49bb-9db7-bf3087c89922 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9b5b2512-01ad-49bb-9db7-bf3087c89922 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=9b5b2512-01ad-49bb-9db7-bf3087c89922 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=9b5b2512-01ad-49bb-9db7-bf3087c89922 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.1, kernel 2.6.20-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=9b5b2512-01ad-49bb-9db7-bf3087c89922 ro quiet splash
initrd		/boot/initrd.img-2.6.20-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-17-generic root=UUID=9b5b2512-01ad-49bb-9db7-bf3087c89922 ro single
initrd		/boot/initrd.img-2.6.20-17-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
rootnoverify	(hd0,0)
makeactive
chainloader	+1

```

---

### Post by rockerboo on 2008-08-21
Is Windows the first partition on the drive? Or the second one.

Right now you have the first parition (hd0,0) being Windows, second being Ubuntu (hd0,1).

---

### Post by CowboyFunk on 2008-08-21
Right windows is in the first partition. Ubuntu second. Then I have a third partition mounted as /home

---

### Post by louieb on 2008-08-21
Everything looks as  it should. Very weird. 
Are you using a splash image?
Some are so dark that its hard to tell what entry is highlighted.

Instead of pressing enter press **e **and make sure you have selected the XP entry. If you have then you can press **b** to boot.

---

### Post by drs305 on 2008-08-21
Just a related note. If you are interested in reducing the number of kernels in your menu.lst I wrote a tutorial on the gui way to do it (StartUp-Manager). It's simple and almost risk-free. See the link in my signature.

---

### Post by caljohnsmith on 2008-08-21
Just to confirm, would you please post the output of:
```
sudo fdisk -lu
sudo grub
grub> geometry (hd0)
grub> quit
```

---

### Post by CowboyFunk on 2008-08-21
sudo fdisk -lu
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1abd1abc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    17093159     8546548+   7  HPFS/NTFS
/dev/sda2        17093160    74991419    28949130   83  Linux
/dev/sda3        74991420   153661724    39335152+  83  Linux
/dev/sda4       153661725   156296384     1317330    5  Extended
/dev/sda5       153661788   156296384     1317298+  82  Linux swap / Solaris

Disk /dev/sdc: 1994 MB, 1994391552 bytes
64 heads, 32 sectors/track, 1902 cylinders, total 3895296 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x417e417d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *         369     1945599      972615+   6  FAT16

```

grub> geometry (hd0)
```
drive 0x80: C/H/S = 9729/255/63, The number of sectors = 156301488, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

```

---

### Post by CowboyFunk on 2008-08-22
halp bump

---

### Post by caljohnsmith on 2008-08-22
CowboyFunk, how about restarting your computer, select the Windows XP entry in the Grub menu, and then hit "e" to edit it. Does it show the following:
```
rootnoverify	(hd0,0)
makeactive
chainloader	+1
```
If it does, then edit the first line so that "rootnoverify (hd0,0)" is simply "root (hd0,0)", push return to save your change, and then hit "b" to boot. Does that work? If not try different values for (hd0,X), but use "root (hd0,X)" and not "rootnoverify (hd0,X)". Each time see if it boots.

---

### Post by SkonesMickLoud on 2008-08-22
When you select Ubuntu, is there any hesitation from grub, or does it go straight to XP?

---

### Post by CowboyFunk on 2008-08-22
> **caljohnsmith said:**
> CowboyFunk, how about restarting your computer, select the Windows XP entry in the Grub menu, and then hit "e" to edit it. Does it show the following:
```
rootnoverify	(hd0,0)
makeactive
chainloader	+1
```
If it does, then edit the first line so that "rootnoverify (hd0,0)" is simply "root (hd0,0)", push return to save your change, and then hit "b" to boot. Does that work? If not try different values for (hd0,X), but use "root (hd0,X)" and not "rootnoverify (hd0,X)". Each time see if it boots.

I tried what you suggested but it didn't work out. I even tried variations on "root (hdX,X)." no success :confused:

> **SkonesMickLoud said:**
> When you select Ubuntu, is there any hesitation from grub, or does it go straight to XP?

Oh you got it mixed up. I can't boot XP at all, but that reminds me- when I select windows xp in grub it does take a few seconds longer than usual then it goes to boot up ubuntu.

---

### Post by louieb on 2008-08-23
I can think of one thing  that would cause that. Somehow you overwrote the sda1 boot sector. 

You have 2 Linux Partitions sda2 and sda3.  You said sda2 is your Ubuntu Linux / (root) partition.  What is sda3 used for? 
Home partition?  data partition? a second Linux / (root) partition?

What it sounds like is that after you install XP -
When you restored grub  you set the / (root)  to (hd0,1) or (hd0,2) 
and then ran **setup (hd0,0)**  when you wanted to run setup (hd0).

That would have over wrote the XP partition boot sector and made it boot whatever is in  sda2 or sda3. 

Think you need to fix your XP boot sector. With the XP install CD boot in recovery mode and run the command** fixboot**.

Good Luck.

---

### Post by CowboyFunk on 2008-08-25
I followed louieb's advice and it turns out he was right. Thanks everyone for helping me.

---

