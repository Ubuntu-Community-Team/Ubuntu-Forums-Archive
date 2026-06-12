---
title: "I want the 2nd HDD to go in stanby automatically,how?"
date: 2014-07-28
forum: Hardware
---

### Post by viktor5 on 2014-07-28
Hi,

I want my 2nd HDD that contains Windows to go in standby automatically,
I already changed the settings of this HDD under preferences--Discs to go standby after 1 minute of inactivity
but it does not work...Why?

I always have to manually put it in standby.

Is there something else I can do to go in standby or even to not start...I don't need it when I'm in the lubuntu partition.

Thank you):P

---

### Post by tgalati4 on 2014-07-28
Try unplugging it.  Do you have any mounts in /etc/fstab?  Do you have any desktop mounts?  Do you have any applications open that accessed any files on the Windows partition?
How many partitions on the drive?  Any swap or data partitions on the drive?  There are several reasons to spin up a drive.  Open a terminal and post the output of:

```
sudo fdisk -l
```

---

### Post by viktor5 on 2014-07-29
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 testine, 63 settori/tracce, 20673 cilindri, totale 312581808 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x24a9a663


Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312575759   156287848+  83  Linux


Disk /dev/sdb: 40.0 GB, 40020664320 bytes
240 testine, 63 settori/tracce, 5169 cilindri, totale 78165360 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0xb5d01cf6


Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    78155279    39077608+   7  HPFS/NTFS/exFAT
sirludwig@sirludwig:~$ 


Here's the sudo fdisk result,
there are not any swap or data partitions on the drive(the 40 GB drive),
when I manually put it in Standby it does never automatically turn on again.

Thanks for your help:KS

---

### Post by viktor5 on 2014-08-01
UP!
please help

---

