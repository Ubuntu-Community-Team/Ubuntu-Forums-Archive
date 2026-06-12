---
title: "Read Only Disk Problem."
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by dangman4ever on 2005-09-11
Hello. 

My mounted 60GB hard drive is seen as a "Read Only Disk". I can't write, edit or move around files in that hard drive. My other mounted hard drive, a 200GB split into two partitions, works fine. I'm using the exact same code in the fstab file:

> /dev/hdb1    /mnt/windows    vfat defaults,auto,rw,users,umask=000
/dev/hdd1   /mnt/windows2    vfat defaults,auto,rw,users,umask=000
/dev/hdd5   /mnt/windows3    vfat defaults,auto,rw,users,umask=000 

hdb1 is my 60GB hard drive
hdd1 and hdd5 are my 200Gb partitions. 

All mounted partitions use the same line but the 60GB is still seen as a "Read only" drive.

Heres what fdisk gave me:

>    Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7297    58613121    c  W95 FAT32 (LBA)

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       12162    97691233+   c  W95 FAT32 (LBA)
/dev/hdd2           12163       24321    97667167+   f  W95 Ext'd (LBA)
/dev/hdd5           12163       24321    97667136    b  W95 FAT32 

I also did " chmod a=rwx /mnt/windows " Butthat didn't work either. i got this error:

> chmod: changing permissions of `/mnt/windows': Read-only file system 

Is there a solution?

---

### Post by mlomker on 2005-09-11
What is the output of **mount** and **dmesg | grep hdb**?

---

### Post by dangman4ever on 2005-09-12
**mount** gets me this:
> /dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hdb1 on /mnt/windows type vfat (rw,nosuid,nodev,umask=000)
/dev/hdd1 on /mnt/windows2 type vfat (rw,noexec,nosuid,nodev,umask=000)
/dev/hdd5 on /mnt/windows3 type vfat (rw,noexec,nosuid,nodev,umask=000)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw) 

**dmesg | grep hdb**:

>     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
hdb: probing with STATUS(0x50) instead of ALTSTATUS(0x00)
hdb: WDC WD600BB-32BSA0, ATA DISK drive
hdb: max request size: 128KiB
hdb: 117231408 sectors (60022 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
hdb: cache flushes not supported

---

### Post by dangman4ever on 2005-09-13
Oh and I just checked the properties out on the 60Gb hard drive,

It gives me this:

**Modified**: Wed 31 Dec 1969 04:00:00 PM PST 

Is that an indication that my hard drive is about to die? Or something is seriously wrong with it.

---

### Post by mlomker on 2005-09-13
Try this command in a terminal window:

**sudo chmod 777 /mnt/windows**.

---

### Post by dangman4ever on 2005-09-15
[QUOTE=mlomker]Try this command in a terminal window:

**sudo chmod 777 /mnt/windows**.[/QUOTE]


Just tried it, didn't work. 

Shoot, I think I might have to reformat that drive.

---

### Post by mlomker on 2005-09-16
Did't help or returned an error?  I assume you're **su**ed to root when you try to write something?

The mount output looks right to me.  I'd omit the **defaults** thing in your fstab because you're customizing everything anyway, but it is being ignored so not a problem.

---

### Post by dangman4ever on 2005-09-18
No error messages were given. I did sued into root. And yeah you're right: the defaults are just a bit vestigial.

I think it may be a problem with the hard drive itself. I used GParted on the 60 GB one and it was unable to read the contents of the file system. So no partitioning could be done. Just to make sure, I tested my 200GB hard drive with GParted. Works fine.

So it must be a problem with the hard drive itself. I'll just wipe it clean and see what happens.

Thank you for trying to help me, mlomker. But unfortunately, nothing works. So clean wipe of the hard drive it is!

---

