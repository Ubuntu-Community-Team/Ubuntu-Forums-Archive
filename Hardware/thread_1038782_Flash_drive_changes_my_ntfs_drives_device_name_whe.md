---
title: "Flash drive changes my ntfs drives device name when i have it in while booting."
date: 2009-01-13
forum: Hardware
---

### Post by powerplayground on 2009-01-13
OK this is seriously annoying. I have 2 ntfs drives. I installed ntfs 3g, and everything is fine until i decided to plug in a flash drive. Now whenever I boot with the flashdrive plugged in it changes the device name's of the ntfs drives, thus making my drives mount to their incorrect directories which breaks ftp. >.<

Here is my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=47a13fa1-68c1-4fbc-b70d-b6f4f14cf32c /               ext3    relatime,erro$
# /dev/sda5
UUID=b3e3e180-8e6f-4ecf-aeb4-b91063feb58d none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /mnt/Storage1 ntfs-3g defaults 0 0
/dev/sdc1 /mnt/Storage2 ntfs-3g defaults 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

And here is the current output of fdisk -l:
```
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

```

How would I make it so that my ntfs drives permanently mount to the chosen directories, and that the device id's dont change?

---

### Post by mikewhatever on 2009-01-14
One way would be to use UUIDs instead of device names, in the manner it's used for your root and swap partitions. Use the following to find out the UUIDs, and backup the current fstab before proceeding.

sudo vol_id -u /dev/sdb1
sudo vol_id -u /dev/sdc1
sudo vol_id -u /dev/sdd1

---

