---
title: "grub issue, unistalling"
date: 2008-10-26
forum: General Help
---

### Post by BlackLLama on 2008-10-26
hello, my problem is i unistalled a partition, now grub says it has an error, and i can't boot any partition,

i have vista as my primary partition
ubuntu as secondary
and ubuntu as a third partition, in which the error derives, to unistall this third partition i simply deleted the partition, 

how can i edit the grub menu file to boot normally with no issues, 

i am writing this while on a nimbleX live cd

---

### Post by BlackLLama on 2008-10-26
can anyone help me re-write the grub menu.lst, or what do i need to do, this is rendering my computer useless

---

### Post by caljohnsmith on 2008-10-26
Try this from your Live CD:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Post the output of all the above commands, and also post:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by BlackLLama on 2008-10-26
all unrecognized commands, error 27

---

### Post by BlackLLama on 2008-10-26
i reinstalled the partition, so i can acess the other ones, i am now running ubuntu

andrew@andrew-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12cd12cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1132548864   566274401    7  HPFS/NTFS
/dev/sda3      1132550370  1465144064   166296847+   5  Extended
/dev/sda5      1255431618  1456533224   100550803+  83  Linux
/dev/sda6      1456533288  1465144064     4305388+  82  Linux swap / Solaris
[U]/dev/sda7      1132550496  1250322884    58886194+  83  Linux
/dev/sda8      1250322948  1255431554     2554303+  82  Linux swap / Solaris[/U]

Partition table entries are not in disk order
andrew@andrew-desktop:~$ 

i need to take the underlined partition from the boot

---

