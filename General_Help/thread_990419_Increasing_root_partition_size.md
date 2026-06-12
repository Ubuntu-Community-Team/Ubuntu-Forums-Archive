---
title: "Increasing root partition size"
date: 2008-11-22
forum: General Help
---

### Post by bff7755a on 2008-11-22
Hello.

I have located only 500 Mb for my "/" partition and now it's full. How can I increase a partition size? I think I have to run Live CD version and use GParted, but I can't increase partition size, because the nex partition (extended) containts some partitions too and I think, I must delete them before changing the root partition.

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4448

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sda1               1          61      489951   83  Linux[/COLOR]
/dev/sda2              62       91201   732082050    5  Extended
/dev/sda5   *          62         122      489951   83  Linux
/dev/sda6             123        2554    19535008+  83  Linux
/dev/sda7            2555        3770     9767488+  83  Linux
/dev/sda8            3771        4256     3903763+  82  Linux swap / Solaris
/dev/sda9            4257        4864     4883728+  83  Linux
/dev/sda10           4865       91201   693501921   83  Linux
```

```
[desktop][mutex]~> df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Red"]/dev/sda1             464M  413M   28M  94% /[/COLOR]
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  216K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.9M  1.7G   1% /dev
tmpfs                 1.7G  332K  1.7G   1% /dev/shm
lrm                   1.7G   30M  1.6G   2% /lib/modules/2.6.24-21-generic/volatile
/dev/sda5             464M   33M  408M   8% /boot
/dev/sda10            651G  334G  285G  55% /home
/dev/sda9             4.6G  138M  4.3G   4% /tmp
/dev/sda6              19G  5.0G   13G  29% /usr
/dev/sda7             9.2G  2.8G  6.0G  32% /var
/dev/sdb1             688G  486G  168G  75% /home/mutex/data
/dev/sdc1             276G   23G  239G   9% /home/mutex/mp3

```

---

### Post by CatKiller on 2008-11-22
> **bff7755a said:**
> I have located only 500 Mb for my "/" partition and now it's full. How can I increase a partition size? I think I have to run Live CD version and use GParted, but I can't increase partition size, because the nex partition (extended) containts some partitions too and I think, I must delete them before changing the root partition.


You're right that you need to use a live cd; you can't change a mounted partition, and you can't unmount /, since that contains the program that you're running.

You're incorrect to think that you need to delete the other partitions. As long as there's some free space somewhere, you can just resize those partitions to get some unpartitioned space. Then it's just a case of dragging the partitions around till you get the unpartitioned space next to the partition you want to expand.

It's quite straightforward. Drag the right-hand end of a partition to resize it. Drag the middle of a partition to move it. Don't forget to resize your extended partition as well as the partitions inside it - it will be displayed as a box around those partitions.

The only other thing to remember is that if you're running from a live cd, your swap partition will probably be used by default. This is great for general use, but a pain if you need to move that partition. ```
sudo swapoff -a
``` will unmount it.

---

