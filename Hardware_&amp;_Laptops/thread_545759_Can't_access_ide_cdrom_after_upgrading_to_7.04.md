---
title: "Can't access ide cdrom after upgrading to 7.04"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by Atrav on 2007-09-08
After upgrading to Feisty I can no longer access my cdrom ide drive.  When I do : 
 ls -l /dev/cdrom it returns lrwxrwxrwx 1 root root 3 2007-09-06 09:08 /dev/cdrom -> hdb.

The drive won't mount and dmesg | tail yields:  hdb: status error: status=0x59 and ide: failed opcode was: unknown and finally hdb: drive not ready for command.

Here is what I get with dmesg:   dmesg | tail
[  739.052000] ide: failed opcode was: unknown
[  739.052000] hdb: drive not ready for command
[  807.148000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
[  807.148000] hdb: status error: error=0x44 { AbortedCommand LastFailedSense=0x04 }
[  807.148000] ide: failed opcode was: unknown
[  807.148000] hdb: drive not ready for command
[ 1088.860000] hdb: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
[ 1088.860000] hdb: status error: error=0x44 { AbortedCommand LastFailedSense=0x04 }
[ 1088.860000] ide: failed opcode was: unknown
[ 1088.860000] hdb: drive not ready for command


I am a fairly new user and need your help.

---

