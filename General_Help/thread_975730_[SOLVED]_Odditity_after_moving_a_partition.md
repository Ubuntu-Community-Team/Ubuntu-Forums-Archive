---
title: "[SOLVED] Odditity after moving a partition"
date: 2008-11-08
forum: General Help
---

### Post by Tony Flury on 2008-11-08
I booted my Laptop using the 8.10 Live CD 
and then used Gparted to moved my 8.0.4 installation from a primary partition /dev/sda2 to a logical partition /dev/sda7
I then created a 2nd logical partition /dev/sda8 on which to install 8.10 

The installation works ok (grub menu is a but odd as it seems to think that I have 8.0.4 on both /dev/sda7 and /dev/sda1 (which is actually a small Windows XP partition.

I can boot 8.10 ok.

When i choose the /dev/sda7 choice on the Grub menu - 8.0.4 boots fine however - here comes the odd part...

1) in GParted there is a warning against /dev/sda7 - saying there is not mount point info - and this is despite the fact that 8.0.4 has booted - I can see all of the aditional applications that i have installed.

2) When i use df i get the following : 

```

> df -Th | grep /dev/sda

/dev/sda2     ext3     31G  7.7G   22G  27% /
/dev/sda6     ext3     76G   16G   56G  22% /home
/dev/sda5  fuseblk     31G  550M   31G   2% /share
/dev/sda1  fuseblk     33G   22G   11G  67% /windows

```

As you can see something still thinks that root is on /dev/sda2 - despite the fact that there is no /dev/sda2 - and the only 8.0.4 image is on /dev/sda7

I know that 8.0.4 is working ok right now - but i guess at some point soon - this will come to bite me - so any help to reset stuff would be greatly appreciated.

---

### Post by logos34 on 2008-11-08
df only shows mounted partitions.

Post output of 

sudo fdisk -l

---

### Post by Tony Flury on 2008-11-08
> 
df only shows mounted partitions.


Thanks for that, but in which case why is /dev/sda2 mounted - when it does not exist - and why is /dev/sda7 not mounted when that is actually where "/" is, and where for example firefox is installed right now.

```

sudo fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4256    34186288+   7  HPFS/NTFS
/dev/sda3           30020       30401     3068415   82  Linux swap / Solaris
/dev/sda4            8121       30019   175903717+   5  Extended
/dev/sda5           16155       20144    32049675    7  HPFS/NTFS
/dev/sda6           20145       30019    79320906   83  Linux
/dev/sda7           12106       16154    32523561   83  Linux
/dev/sda8            8121       12105    32009449+  83  Linux

Partition table entries are not in disk order

```

---

### Post by logos34 on 2008-11-08
yeah, looks pretty odd

what about:

cat /etc/fstab

---

### Post by Tony Flury on 2008-11-08
ah ha - I spotted it 

/dev/sda2 was still listed in /etc/fstab - which of course it would be - because moving the partition would not edit /etc/fstab :-) doh !

pretty amazing that it booted at all when "/" was not mounted.

---

### Post by logos34 on 2008-11-08
Did you also remember to change 'kernel' line in /boot/grub/menu.lst? 

If 8.04 / partition is now sda7, you want

> **root (hd0,[COLOR=Red]6[/COLOR])**

(also edit '**groot**' line to match)

You might want to rewrite grub to MBR just for good measure:
[B]
sudo grub[/B]

> grub> **find /boot/grub/stage1**
(should output 'hd0,6' and 'hd0,7')
grub> **root (hd0,6)**
grub> **setup (hd0)**
grub> **quit**


---

