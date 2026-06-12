---
title: "partition won't mount, &quot;short read&quot; errors"
date: 2009-10-17
forum: Hardware
---

### Post by sander314 on 2009-10-17
I have a partition which won't mount, and keeps giving errors on every command I try.

**Patient history:**
- was on a dualboot machine with most of the HD space dedicated to windows. 
- As I started to use linux more I ran out of space and used gparted to shrink the windows partition and get an extra linux partition.
- formatted as ext3.
- used it for over a year, no problems.

- recently bought a new pc, placed this HD in as an extra one.
- all partitions mounted ok, copied some data off it.
- (possibly deleted some things as well. not quite sure.)
- (at this point or afterwards there was possibly a hard crash + hard reboot.  can't quite remember how close this was, but the partition was possibly still mounted.)
- some time afterwards I noticed the partition had disappeared.
- other partitions on the same disk still work.

**Diagnostic tests:**
[IMG]http://img96.imageshack.us/img96/263/gparted.png[/IMG]

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae65ae65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11443    91915866    7  HPFS/NTFS
/dev/sdb2           28048       30410    18980797+  83  Linux
/dev/sdb3           30411       30515      843412+   5  Extended
/dev/sdb4           11444       28047   133371630   83  Linux
/dev/sdb5           30411       30515      843381   82  Linux swap / Solaris

Partition table entries are not in disk order

$ sudo e2fsck -f /dev/sdb4
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb4
Could this be a zero-length partition?

$ sudo debugfs /dev/sdb4 -w
debugfs 1.41.4 (27-Jan-2009)
/dev/sdb4: Attempt to read block from filesystem resulted in short read while opening filesystem

$ sudo e2fsck -f /dev/sdb4 -b 32768
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdb4: Attempt to read block from filesystem resulted in short read while reading block 1545
/dev/sdb4: Attempt to read block from filesystem resulted in short read reading journal superblock
e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sdb4

**What is the problem here and how can I fix it?**
- Is it physically crashing? If not I could just reformat as most of the data is either backed up or not that important, although I would prefer not to.

---

