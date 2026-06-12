---
title: "Harddrive went missing, need to get it back"
date: 2008-10-31
forum: General Help
---

### Post by demetrius_of_pharos on 2008-10-31
One of my internal SATA harddrives stopped working rather randomly a couple days ago. On boot, the message that comes up says there is a bad superblock but when I am in Ubuntu, the partition itself is not recognized at all. (This is not my main harddrive.) I have also tried a new SATA cable.

As much relevant info as I can think of:
The drive is ext3 and has only one partition. 500gb, WD I think.
Was once /dev/sdb, sdb still shows but the partition doesnt.
Im running Ubuntu 8.04 64bit

dmesg gave me no info on sdb at all.
gparted doesnt recognize sdb.

ls /dev/sd*:
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdc  /dev/sdc1  /dev/sdd  /dev/sdd1  /dev/sde  /dev/sde1

fstab:
# /dev/sdb1
UUID=6789e7f2-cde4-475f-b159-da7ec8ac9fce /PATH_TO_MOUNT        ext3    defaults 0 2

e2fsck -C0 -p -f -v /dev/sdb1:
e2fsck: No such file or directory while trying to open /dev/sdb1
/dev/sdb1:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

e2fsck -b 8193 /dev/sdb
e2fsck: No medium found while trying to open /dev/sdb
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fdisk /dev/sdb -l:
Error: Error opening /dev/sdb: No medium found
   r   Retry
   c   Cancel

I am all out of ideas. Can anyone help me recover/mount this drive?

---

### Post by cariboo on 2008-10-31
It sounds like your drive has gone defective. I would suggest you download the hard drive manufacturers diagnostic software and see if it detects your hard drive.

Jim

---

### Post by lH)4~mK0e on 2008-10-31
> fstab:
# /dev/sdb1
UUID=6789e7f2-cde4-475f-b159-da7ec8ac9fce /PATH_TO_MOUNT        ext3    defaults 0 2

Wait, does your fstab really look like this?  /dev/sdb1 is commented out.

Mine appears to be this way as well, probably udev. Can you see it with the live cd?

---

### Post by demetrius_of_pharos on 2008-10-31
> **miwarlock002 said:**
> Wait, does your fstab really look like this?  /dev/sdb1 is commented out.

Mine appears to be this way as well, probably udev. Can you see it with the live cd?

Yes, it looks like that but its supposed to. The /dev/sdb1 is human readable, the UUID below it is a unique ID assigned to the partition. According to what I have found, its better to have UUID in fstab, especially for  external drives like USB, because if they are plugged in/turned on/recognized in a different order on boot, they still mount in the same places. They may not if you just go by /dev/DEVICE.


EDIT:
I havent tried the Ubuntu Live CD or the System Recover CD yet, but as I said, even running gParted or TestDisk the drive doesnt get recognized.

---

### Post by lH)4~mK0e on 2008-11-01
Then the only other possibilities that come to mind are a flaky or recently updated BIOS, or the drive may be failing.  I would suggest doing a google search for "ultimate boot cd" as they have just about all of the hard drive manufacturer testing utilities.  A Basic or Quick test should be able to tell you if the drive has any errors.

---

### Post by demetrius_of_pharos on 2008-11-04
Turns out it was a cable problem after all - at least, it seems to have been. While installing a new sound card, I noticed the data cable was loose. Jiggled it and it seems to be working again.

Thank you all for your help and suggestions.

---

