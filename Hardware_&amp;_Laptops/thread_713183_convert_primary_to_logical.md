---
title: "convert primary to logical"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by tuxandpuffy on 2008-03-02
Hello, I have a primary partition containing ubuntu (the entire /), empty space and an extended partition containing a logical swap partition, how do I convert my primary partition to logical and include part of the empty space in the extended?
thanks to anyone who could help me

My harddisk looks like this (sorry I didn't find how to upload the screenshot I made of gparted):

FAT32 Primary partition (contains my personal datas)
empty space (I want to leave it empty but put a part of it in the extended)
EXT3 Primary partition (contains ubuntu 7.10)
extended:
       -linux-swap partition

result of sudo fdisk -l
> 
Disque /dev/sda: 80.0 Go, 80026361856 octets
255 heads, 63 sectors/track, 9729 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2b935ad

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1        4080    32765008+   c  W95 FAT32 (LBA)
La partition 1 ne se termine pas sur une frontière de cylindre.
/dev/sda2   *        6743        9492    22089375   83  Linux
/dev/sda3            9493        9729     1903702+   5  Extended
/dev/sda5            9493        9729     1903671   82  Linux swap / Solaris


I've looked in forums and documentation and was surprised not to find anything because it must be a rather common problem, so sorry if I duplicated an already existing post :).

precision: there was formerly no empty space, I resized my ubuntu partition from the left (because my purpose is to install a new system)
precision: the swap takes the whole extended partition

---

### Post by arimaniac on 2008-03-03
Hello there

Well I would recommend downloading the Gnome Partition Editor.

> GParted uses libparted to detect and manipulate devices and partition
tables while several (optional) filesystem tools provide support for
filesystems not included in libparted.

To download and install type in terminal:

```
sudo apt-get install gparted
```

[B]BE CAREFUL WHEN OPERATING ON PARTITIONS
A WRONG CONFIGURATION COULD DISABLE YOUR SYSTEM[/B]

Hope this helps

Good luck!!!

---

### Post by tuxandpuffy on 2008-03-03
Thanks for the reply, but as written in my initial post, I am already using gparted (in a livecd), the problem is, I don't know how to convert an existing primary partition to a logical one, without having to erase it (I don't want to reinstall my ubuntu). Thanks anyway :)

---

