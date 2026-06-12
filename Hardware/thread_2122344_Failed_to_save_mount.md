---
title: "Failed to save mount"
date: 2013-03-04
forum: Hardware
---

### Post by rallysquirrel on 2013-03-04
I had an OS partition that I hosed due to stupid mistake (it was late at night and and I was trying to fix couchpotato after it stopped working after reboot).
 I had a RAID 1 with 2GB drives with **ext4** filetype. It is filled with 1.8GB of data so I'd like not to reformat it.
I reinstalled the OS and the raid got recognized, however I'm unable to mount. Using webmin (i am a noob) I see the following:

[COLOR=#696969][I]/media/NAS 
Old Linux Native Filesystem (ext2) [/I][/COLOR](used to be ext4 before I hosed the OS)[COLOR=#696969][I]
RAID device 0 
In Use?     No 
Saved?      Yes[/I][/COLOR]


 
When I try to mount the array, I get the following error:

[COLOR=#696969][I]Failed to save mount : Mount failed : 
mount: wrong fs type, bad option, bad superblock on /dev/md0, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail  or so[/I][/COLOR]

running sudo fsck /dev/sda gives the following output
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?[B]

Here's more information[/B]
[COLOR=#696969][I]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/md0 doesn't contain a valid partition table
Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table
Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000[/I]
[/COLOR]

---

