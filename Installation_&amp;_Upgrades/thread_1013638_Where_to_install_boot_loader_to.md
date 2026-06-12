---
title: "Where to install boot loader to?"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by niranjanpm on 2008-12-17
Hi
I am trying to install ubuntu 8.10 on my machine. I already have Windows XP on it. I created the new partitions for /, /home and swap. 
On the last step, i am unsure where to install the boot loader to, the documentation say "install to MBR", the deafult option in the menu i get is (hd0,0).

>sudo fdisk -l gives me:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37b237b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16708   134206978+   f  W95 Ext'd (LBA)
/dev/sda2   *       16709       19456    22073310    7  HPFS/NTFS
/dev/sda5               1         243     1951834+  82  Linux swap / Solaris
/dev/sda6            5100       10198    40957686    7  HPFS/NTFS
/dev/sda7           10199       16708    52291543+   7  HPFS/NTFS


Where should i install boot loader to? (hd0,0) the default option of any other?

---

### Post by Elfy on 2008-12-17
yes, that will be fine - just let it do as it wishes and don't worry about the advanced options

---

### Post by joff13 on 2008-12-17
> **niranjanpm said:**
> Hi
I am trying to install ubuntu 8.10 on my machine. I already have Windows XP on it. I created the new partitions for /, /home and swap. 
On the last step, i am unsure where to install the boot loader to, the documentation say "install to MBR", the deafult option in the menu i get is (hd0,0).

Where should i install boot loader to? (hd0,0) the default option of any other?

Hi,
if I were you I would install it in the Master boot record (MBR)
much better to me

have fun

---

