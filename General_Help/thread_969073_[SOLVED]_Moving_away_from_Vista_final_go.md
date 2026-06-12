---
title: "[SOLVED] Moving away from Vista final go"
date: 2008-11-03
forum: General Help
---

### Post by d4v1dv00 on 2008-11-03
Hi there,

I had been dual booting Vista and Ubuntu for a long time and now i had decided to totally ditch Vista.

I had modified GRUB to remove Vista startup entry but i still have one important question: How do I reclaim those partition from vista? Here is my current drive map:
```

/dev/sda1   *           1        9773    78499572    7  HPFS/NTFS
/dev/sda2            9774        9967     1558305   82  Linux swap / Solaris
/dev/sda3            9968       10575     4883760   83  Linux
/dev/sda4           10576       24321   110414745   83  Linux

```
I wish to reclaim the vista partition (/dev/sda1) without require to reinstall ubuntu. my mount point of /dev/sda3 to / and /dev/sda4 to /home

Please advise.

TQ

d4v1dv00

---

### Post by eldragon on 2008-11-03
you need to install gparted
```

$ sudo apt-get install gparted

```
and run it with admin privileges.. thats the graphic way of doing things..

if you are bold enough, just use fdisk. :D

there you can move, resize, and do all kind of things. although if you plan to resize a mounted partition...this might be quite tricky. best shot is to do this from a livecd. (install gparted there too)

---

### Post by WRDN on 2008-11-03
> **eldragon said:**
> you need to install gparted
```

$ sudo apt-get install gparted

```
and run it with admin privileges.. thats the graphic way of doing things..

if you are bold enough, just use fdisk. :D

there you can move, resize, and do all kind of things. although if you plan to resize a mounted partition...this might be quite tricky. best shot is to do this from a livecd. (install gparted there too)

You can't change the partitions (aside from sda4) from the Ubuntu installation. Windows is on sda1, and to change this, you have to unmount all partitions with a higher number (sda2, sda3 and sda4)- this would mean unmounting the root partition, which cannot be done when it is in use.

You need to modify the partitions from a LiveCD- if you have the Ubutu LiveCD, then boot from it, and open GParted which is preinstalled (System > Administration > GParted/ Partition Editor).

---

### Post by adieb on 2008-11-03
yes you can use gparted to resize. but you really should take a backup. it is possible, that it messes up your partition table...

Why not just  "sudo mkfs.ext4 /dev/sda1"?
After that you just need a entry in /etc/fstab/ to where it should be mounted.
Now you have an extra "hdd" which you can use for media/backups/whatever...

---

### Post by d4v1dv00 on 2008-11-04
> **adieb said:**
> yes you can use gparted to resize. but you really should take a backup. it is possible, that it messes up your partition table...

Why not just  "sudo mkfs.ext4 /dev/sda1"?
After that you just need a entry in /etc/fstab/ to where it should be mounted.
Now you have an extra "hdd" which you can use for media/backups/whatever...

That was a good idea but under /dev/sda3 where my mount of / now running out of space. My /home (/dev/sda4) still have plenty of space left. So its better i resize to expand /dev/sda3 first, only if later i need more space for /dev/sda4 then only i make space for the later.

---

### Post by d4v1dv00 on 2008-11-04
> **WRDN said:**
> You can't change the partitions (aside from sda4) from the Ubuntu installation. Windows is on sda1, and to change this, you have to unmount all partitions with a higher number (sda2, sda3 and sda4)- this would mean unmounting the root partition, which cannot be done when it is in use.

You need to modify the partitions from a LiveCD- if you have the Ubutu LiveCD, then boot from it, and open GParted which is preinstalled (System > Administration > GParted/ Partition Editor).

Thanks for the advices. This is my plan:

1. Remove /dev/sda1 partition using GPartEd

2. Move /dev/sda2 (swap) to the beginning of the disk, then it became /dev/sda1

3. Move /dev/sda3 (/) after swap and resize to gain free space (let's say 60% of those)

4. Move /dev/sda4 (/home) after / and resize to gain the rest behind till end of disk

After the move and resize
=========================

1. /dev/sda2 became /dev/sda1
2. /dev/sda3 became /dev/sda2
3. /dev/sda4 became /dev/sda3

Sound like this ain't gonna work huh? So I do have to retain /dev/sda1?

To the extreme case i just remain /dev/sda4 (/home) and format the /dev/sda1 + /dev/sda2 + /dev/sda3 and install Ubuntu 8.10 !!!??? LoL

---

### Post by d4v1dv00 on 2008-11-05
ok, update.

my plan works except the /dev/sda2 never turned to /dev/sda1. anyhow, ubuntu is at least brilliant than Windows any edition since '95

---

