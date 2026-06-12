---
title: "[SOLVED] Added a hard drive but it won't mount"
date: 2008-09-01
forum: General Help
---

### Post by beaver29 on 2008-09-01
i was running gutsy as a virtual machine under VMWare player 2.0.1. on a windows XP host.  i tried to install a new package a few days ago and it trashed something on my disk.  now i can't boot that machine.  i'm trying to recover the data i had on the hard disk.

i added the corrupted hard disk to another virtual machine (Hardy Jeos) but i get an error when i try to mount the corrupted drive.  i've shown the output of some relevant commands below.  i get pretty much the same error when i try to mount this corrupted disk on another virtual machine running at different distro (Kate-OS 3.6, linux 2.6).

any ideas why mount wouldn't work?  does it need some options?  or can anyone think of some other way to recover the data from this drive?  i really need the data so any thoughts would be much appreciated!


 $ sudo mkdir /Junk
 $ sudo mount -text2 /dev/sdc2 /Junk
mount: wrong fs type, bad option, bad superblock on /dev/sdc2,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 $ dmesg | tail -n3
[  407.074979] attempt to access beyond end of device
[  407.075062] sdc2: rw=0, want=4, limit=2
[  407.075194] EXT2-fs: unable to read superblock

 $ sudo fdisk -l
Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00018344
   Device Boot      Start        End      Blocks   Id  System
/dev/sda1   *           1       1044     8385898+  83  Linux

Disk /dev/sdb: 268 MB, 268435456 bytes
255 heads, 63 sectors/track, 32 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024ea7
   Device Boot      Start        End      Blocks   Id  System
/dev/sdb1               1         32      257008+  82  Linux swap / Solaris

Disk /dev/sdc: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000091e1
   Device Boot      Start        End      Blocks   Id  System
/dev/sdc1   *           1         31      248976   83  Linux
/dev/sdc2              32       1044     8136922+   5  Extended
/dev/sdc5              32       1044     8136891   8e  Linux LVM


 $ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: VMware,  Model: VMware Virtual S Rev: 1.0
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: VMware,  Model: VMware Virtual S Rev: 1.0
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi0 Channel: 00 Id: 02 Lun: 00
  Vendor: VMware,  Model: VMware Virtual S Rev: 1.0
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi2 Channel: 00 Id: 02 Lun: 00
  Vendor: NECVMwar Model: VMware IDE CDR10 Rev: 1.00
  Type:   CD-ROM                           ANSI  SCSI revision: 05

 $ cat /proc/partitions
major minor  #blocks  name
   8     0    8388608 sda
   8     1    8385898 sda1
   8    16     262144 sdb
   8    17     257008 sdb1
   8    32    8388608 sdc
   8    33     248976 sdc1
   8    34          1 sdc2
   8    37    8136891 sdc5

---

### Post by oldos2er on 2008-09-01
See if running fsck on it helps. "fsck /dev/sdc2"

---

### Post by beaver29 on 2008-09-01
OK, that was worth a try, thanks.  here's  what i got:

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdc2
Could this be a zero length partition?

the exit code i got was "8" which means "Operational error".  when i saw the "Could this be a zero length partition?", it made me think the output of "cat /proc/partitions" (posted above) was fishy because it says /dev/sdc2 has one block.  but i checked another gutsy virtual machine that is working correctly and it's output is identical. evidently that's normal.

any other ideas?

---

### Post by knattlhuber on 2008-09-01
> **beaver29 said:**
> 
sudo mount -text2 /dev/sdc2 /Junk


Shouldn't that read

```
sudo mount -t ext2 /dev/sdc2 /Junk
```

(Space between t and ext2)

---

### Post by beaver29 on 2008-09-01
yeah, prolly.  :-)  maybe "mount" doesn't care or it just used the default which is EXT2 anyway.  in any case, it's obvious from the dmesg output that it was trying to mount the partition as EXT2 so maybe i got lucky.  :-)

---

### Post by beaver29 on 2008-09-03
OK, i've made some progress.  i tried mounting a known good VMware virtual disk using the process shown above and got the same results.  so i realized there wasn't a problem with the disk.  i tried running fsck on every partition in /dev/sdc (the disk i'm trying to mount) and when i ran it on sdc5 it complained that it couldn't find something called "fsck.lvm2pv".  that error msg made me finally take notice that this partition is LVM (logical volume manager).

so it looks like my problem is that mounting an LVM partition is not as straightforward as "mount -t LVM /dev/sdc5 /MountDirectory".  i've seen a webpage or two explaining a convoluted process for mounting an LVM volume in VMWare but they seem to assume Ubuntu is the host and VMWare server is installed under Ubuntu.  i'm running Ubuntu as a guest so i'm trying to find an easier way.  if anybody has seen a thread that explains it, i'd be really, really grateful for a pointer.

---

### Post by beaver29 on 2008-09-08
yup, it turns out my problem was mounting a Linux Logical Volume Manager
(LVM) partition.  i followed the steps on this site:

[http://www.linux-sxs.org/storage/fedora2ubuntu.html]("http://www.linux-sxs.org/storage/fedora2ubuntu.html")

and i was able to mount my disk.  i removed one corrupted file and now i can boot my machine again.  sweet!  this site

[http://www.howtoforge.com/linux_lvm]("http://www.howtoforge.com/linux_lvm")

is a helpful introduction for LVM newbies.

---

