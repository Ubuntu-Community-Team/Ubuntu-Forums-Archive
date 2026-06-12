---
title: "Home partition periodically gives mount error on boot"
date: 2011-04-06
forum: Hardware
---

### Post by GeraldNunn on 2011-04-06
I recently installed Ubuntu on my laptop in a dual boot setup with Windows. I have an SSD (1) and a hard drive (2) with the partitions setup as follows:

sda1: Windows Root
sda2: Linux Root (/)

sdb1: Windows Data
sdb2: Linux Data
sdb3: Linux Swap

Everyone so often when I boot I get a mount error message prompting me to Ignore, Skip or Abort. If press I to ignore everything boots fine and there doesn't appear to be any issues. Here is my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=8f3e03ad-3230-4ef7-850d-d898bbbe004d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
# Commented out by Dropbox
# UUID=12e2b1f8-e0c1-48e7-b439-2c1bec0e1dc4 /home           ext4    defaults        0       2
# swap was on /dev/sdb3 during installation
UUID=6773d499-1837-456f-935a-890d9b87b2d0 none            swap    sw              0       0
UUID=12e2b1f8-e0c1-48e7-b439-2c1bec0e1dc4 /home ext4 defaults,user_xattr 0 2

```

And here is the error that shows in the boot log:

```

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck.ext4: No such file or directory while trying to open /dev/disk/by-uuid/12e2b1f8-e0c1-48e7-b439-2c1bec0e1dc4
/dev/disk/by-uuid/12e2b1f8-e0c1-48e7-b439-2c1bec0e1dc4: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

mountall: fsck /home [479] terminated with status 8
mountall: Unrecoverable fsck error: /home
/dev/sda2: clean, 208652/3981312 files, 2036257/15898368 blocks
Ignoring errors with /home at user request
 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

[74G[ OK ]
 * Setting sensors limits       [80G 

```

---

### Post by GeraldNunn on 2011-04-15
I'm still looking for help with this as the issue is starting to get annoying.

---

### Post by GeraldNunn on 2011-04-20
Still getting this every so often and would appreciate some help, would prefer not to do a re-install.

---

### Post by lenooh on 2011-05-24
I have the same problem, with a similar setup: SSD and HDD combination.
It happens about every 10th boot, that I get the error message telling me that there was a serious error when trying to mount the filesystem on HDD. If I ignore the error, everything seems to be OK. This happens on Ubuntu 10.10 and 11.04.

I would guess this is a bug in upstart.

I will try to cirumvent the error by creating a script that "manually" mounts my HDD filesystem only when I log into gnome (I do not need those files before that). I will let you know if it helps...

---

### Post by Rincage on 2011-07-23
Any solution to this yet as I have the same problem. Really annoying as I run the server with no keyboard attached and it's not very accessible.

---

