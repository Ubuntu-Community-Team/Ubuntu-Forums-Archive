---
title: "Can't format external hard drive"
date: 2014-09-10
forum: Hardware
---

### Post by bradhaack on 2014-09-10
I have a Maxtor USB hard drive that was formated for Mac.  I'm trying to reformat it to ext.   KDE Partition Manager gives me errors but no details.  gparted gave me a slew of errors, but it seemed to get through to the end.
Here are the error messages, edited to delete the dupes.
```
gpartedbin:20764): GLib-CRITICAL **: Source ID 7 was not found when attempting to remove it
(gpartedbin:20764): GLib-CRITICAL **: Source ID 6 was not found when attempting to remove it
...
Error fsyncing/closing /dev/sdb: Remote I/O error
...
(gpartedbin:20764): GLib-CRITICAL **: Source ID 468 was not found when attempting to remove it
...
(gpartedbin:20764): GLib-CRITICAL **: Source ID 653 was not found when attempting to remove it
Error fsyncing/closing /dev/sdb: Remote I/O error
...
(gpartedbin:20764): IBUS-WARNING **: The owner of /home/brad/.config/ibus/bus is not root!
Error fsyncing/closing /dev/sdd: Remote I/O error
Remote I/O error during write on /dev/sdd
Error fsyncing/closing /dev/sdd: Remote I/O error
(gpartedbin:20764): GLib-CRITICAL **: Source ID 3527 was not found when attempting to remove it
(gpartedbin:20764): GLib-CRITICAL **: Source ID 3526 was not found when attempting to remove it
Error fsyncing/closing /dev/sdd: Remote I/O error
Remote I/O error during write on /dev/sdd
```
It shows up under DEVICES in File Manager, but when trying to mount 
```
Failed to mount "Maxtor2".

Error mounting /dev/sdd1 at /media/brad/Maxtor2: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdd1" "/media/brad/Maxtor2"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
```
From dmesg:
```
[ 8001.592012] end_request: critical target error, dev sdb, sector 0
[ 8002.252738] end_request: critical target error, dev sdd, sector 0
[ 8002.968337] end_request: critical target error, dev sdd, sector 0
[ 8014.569006] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
[ 8015.755789] end_request: critical target error, dev sdd, sector 0
[ 8020.067900] end_request: critical target error, dev sdd, sector 96733216
[ 8020.067944] Aborting journal on device sdd1-8.
[ 8020.625214] EXT4-fs error (device sdd1): ext4_journal_check_start:56: Detected aborted journal
[ 8020.625222] EXT4-fs (sdd1): Remounting filesystem read-only
[ 8124.254903] EXT4-fs error (device sdd1): ext4_put_super:791: Couldn't clean up the journal
[ 8126.653189] end_request: critical target error, dev sdd, sector 0
[ 8126.653233] JBD2: recovery failed
[ 8126.653240] EXT4-fs (sdd1): error loading journal
```

Since I'm having similar issues with an ext encrypted drive I thinking but, but not sure.

---

### Post by ajgreeny on 2014-09-10
Perhapd you need hfsplus package installed before you can format a mac drive.
Not sure why that would be so, but it is needed to mount and read a mac drive, so just maybe to format it as well?

---

### Post by bradhaack on 2014-09-10
I hooked it to the mac & reformatted it as fat32, now I can use it at least.  I don't understand why gparted couldn't partitiion and format it.

---

