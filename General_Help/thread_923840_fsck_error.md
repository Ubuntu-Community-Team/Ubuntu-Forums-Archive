---
title: "fsck error"
date: 2008-09-18
forum: General Help
---

### Post by earthtux on 2008-09-18
my computer has 1GB physical memory
my fdisk -l
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19d9516a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23849   191567061   83  Linux
/dev/sda2           23850       24321     3791340    5  Extended
/dev/sda5           23850       24321     3791308+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4       32098+   6  FAT16
/dev/sdb2   *           5        4862    39021885    7  HPFS/NTFS

```
i am trying to run fsck on a usb external hard disk(160GB)
cause I cant mount it
but when i got a error message at the end of pass1 called:
memory allocation error

I followed this link to setup a cache directory for e2fsck
[http://www.nabble.com/2GB-memory-limit-running-fsck-on-a-%2B6TB-device-td17737880.html](http://www.nabble.com/2GB-memory-limit-running-fsck-on-a-%2B6TB-device-td17737880.html)

but i got the same error

is there any way to solve this ?
Thanks in advance!

---

### Post by nitro_n2o on 2008-09-18
why can't you mount the usb?
do you get any error or it does not even show up on your system... 

as soon as you put the usb stick some lines will be added /var/log/syslog with some random stuff about the usb you entered.. if you don't see this, then fsck can't do anything about it

---

### Post by earthtux on 2008-09-18
> **nitro_n2o said:**
> why can't you mount the usb?
do you get any error or it does not even show up on your system... 

as soon as you put the usb stick some lines will be added /var/log/syslog with some random stuff about the usb you entered.. if you don't see this, then fsck can't do anything about it

thank you for your reply,
yes it told me the disk is not clean and i need to use fsck to fix the inode or something
that's why i tried to use fsck on that drive
i can see it in my fdisk -l
Sorry the previous one is b4 i plug in the usb hard drive
and now i am using fsck.ext3 -c on it(-c works)
it has been over 10 hours and it still running
To my knowledge, -c is only a read mode, i doubt it can really fix the disk
Am i wrong?

---

### Post by earthtux on 2008-09-20
after 20 hours of running
fsck -c on my 160GB hardisk
now in my fdisk -l 
the partitions on it is totally gone
when i tried to run fsck again
I got this

error:
bad magic number in super-block while trying to open /dev/sdc1

eeek!

---

