---
title: "2nd HD in my pc"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by WGH on 2005-10-21
Hi!
I'm new in using Ubuntu Linux, and Linux in general!
My PC has 2 HD, but only the 1st is seen from Ubuntu.

In the 2nd i've got all my mp3s and my documents: how can I use them!?

Thanks,
WGH...

---

### Post by arubin on 2005-10-21
Have you checked if it is in /media/hdb?

---

### Post by The Warlock on 2005-10-21
You probably never mounted it. What filesystem is it running?

---

### Post by WGH on 2005-10-21
This is what I see if I run
```
sudo fdisk -l
```
Disk /dev/hda: 2111 MB, 2111864832 bytes
255 heads, 63 sectors/track, 256 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         241     1935801   83  Linux
/dev/hda2             242         256      120487+   5  Esteso
/dev/hda5             242         256      120456   82  Linux swap / Solaris

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
16 heads, 63 sectors/track, 119150 cylinders
Units = cilindri of 1008 * 512 = 516096 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      119149    60051064+   7  HPFS/NTFS

WGH...

---

### Post by WGH on 2005-10-23
up!
Help me please!

WGH...

---

### Post by curien on 2005-10-23
$ sudo mkdir /mnt/drive
$ sudo mount /dev/hdb1 /mnt/drive -t ntfs

If that works for you (at that point you may only be able to examine the drive as root), do

$ cd
$ sudo umount /mnt/drive

Then do
$ man fstab
and
$ man mount

to find out how to add an entry to your /etc/fstab file to allow you to mount the drive as a normal user.

---

### Post by WGH on 2005-10-23
Thanks a lot!
I had found some instructions and I've resolved the problem.
Thanks again!!!

WGH...

---

