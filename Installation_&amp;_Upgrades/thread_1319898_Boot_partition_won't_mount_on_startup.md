---
title: "Boot partition won't mount on startup"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by cknight on 2009-11-08
I've just upgrade from Jaunty to Karma.  My latest problem is that my boot partition (and possibly swap) is failing to automount on startup which is causing serious issues on startup.  Specifically I am getting "One or more of the mounts listed in /etc/fstab cannot yet be mounted:" and goes on to list my boot and swap partitions.  If I drop to the recovery shell and type:
```
sudo mount -t ext2 /dev/sda1 /boot
``` this will successfully mount the boot partition and dropping out of the recovery shell will allow me to continue my boot sequence more or less successfully.  How can I change my fstab file to mount my boot partition properly?  FYI, my boot is on a separate partition of type ext2.  Here's fstab in its current state (which appears to me to be unmodified by the upgrade):
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=00ab043e-08e4-49d4-8e74-a5e45c9b9fe3 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=06c0371d-4fd7-4003-81fe-fdfa70ca495f /boot           ext2    relatime        0       2
# /home was on /dev/sda7 during installation
UUID=1b2d062a-b2c3-491e-8843-336b306866d1 /home           ext4    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=63634451-7b03-40cc-83f7-1b55d7498641 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb5 /data ext4 defaults 0 0

```
Any help most appreciated! :)

---

### Post by cknight on 2009-11-10
gentle bump... still struggling with this one.

---

### Post by oldfred on 2009-11-10
fstab is using UUID's which is preferred but when you manually mount you use sda1, so is the UUID correct?

If you run mount -a  to rerun the fsab, do you get any error messages?

---

### Post by cknight on 2009-11-10
> **oldfred said:**
> fstab is using UUID's which is preferred but when you manually mount you use sda1, so is the UUID correct?

If you run mount -a  to rerun the fsab, do you get any error messages?

Thanks, this was just the help I needed.  'mount -a' yeilds:

```
mount: special device UUID=06c0371d-4fd7-4003-81fe-fdfa70ca495f does not exist
```

which led me to this bug report: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/428318]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/428318") which describes poor identification of a partition which has multiple knock on effects.  I shall try the fix mentioned in it tonight and see if it helps.  Thanks again!

---

