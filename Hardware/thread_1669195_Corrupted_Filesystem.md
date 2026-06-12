---
title: "Corrupted Filesystem?"
date: 2011-01-17
forum: Hardware
---

### Post by cleverbubbles123 on 2011-01-17
Hi guys.
My Eee PC 901 (with 2 internal SSD's, 8GB and 4GB) went halfway into sleep mode (i.e. screen blanked and would not respond) and I couldn't wake it up again. I held down the power button, and rebooted. Upon boot, I got the message that Ubuntu (10.10) was unable to mount home and asked me to either press S or M. I pressed S for skip, and after logging in I received many error messages about not writing to /home etcetera. My home directory is unencrypted on and 8GB SDHC card made by Kingston. I removed the card and put it into my main Ubuntu PC. It told me to 'clean up' the file system as well as other error and mount messages. I think the filesystem is XFS on the SD card.

Have I lost all my files forever? Something less serious? Any help at all is greatly appreciated!
Thanks in advance.
[-o<

---

### Post by cleverbubbles123 on 2011-01-17
bump

---

### Post by cleverbubbles123 on 2011-01-17
bump

---

### Post by psusi on 2011-01-17
Boot from the livecd and fsck the filesystem.  Something like:

sudo e2fsck -fy /dev/sda1

---

### Post by cleverbubbles123 on 2011-01-17
> **psusi said:**
> Boot from the livecd and fsck the filesystem.  Something like:

sudo e2fsck -fy /dev/sda1
ubuntu@ubuntu:~$ sudo e2fsck -fy /dev/sdd1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -b 8193 -fy /dev/sdd1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by cleverbubbles123 on 2011-01-17
> **psusi said:**
> Boot from the livecd and fsck the filesystem.  Something like:

sudo e2fsck -fy /dev/sda1
ubuntu@ubuntu:~$ sudo e2fsck -fy /dev/sdd1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -b 8193 -fy /dev/sdd1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Bad magic number in super-block while trying to open /dev/sdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by cleverbubbles123 on 2011-01-17
remember that the filesystem is XFS not ext2/3/4

---

