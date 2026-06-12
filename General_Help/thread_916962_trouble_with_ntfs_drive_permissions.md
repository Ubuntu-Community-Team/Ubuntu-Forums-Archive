---
title: "trouble with ntfs drive permissions"
date: 2008-09-11
forum: General Help
---

### Post by RiTarDid on 2008-09-11
I'm having trouble with my ntfs drive (/dev/sdb1).  I've manually added the "/dev/sdb1"
line to /etc/fstab to mount the drive on startup, but now I can only access the drive's 
files as root.  How can I automount this drive with read/write permissions for desktop users?

my fstab looks like this:                                                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f2a9184f-b016-42c7-a248-0117c843c3f4 /               ext3    
relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=79bafdac-2138-4f9d-a4ee-0be9ad14140d none            swap    sw    0       0
/dev/sdb1       /media/disk     ntfs    defaults,umask=007,noatime      0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0     0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0      0

output from fdisk -l looks like this:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1df87c1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+  83  Linux
/dev/sda2           10199       12749    20480000    7  HPFS/NTFS
/dev/sda3           12749       38914   210168832    7  HPFS/NTFS
/dev/sda4            9727       10198     3791340    5  Extended
/dev/sda5            9727       10198     3791308+  82  Linux swap / 
Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x254c809d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312566784    7  HPFS/NTFS


Thanks in advance.

---

### Post by HalPomeranz on 2008-09-11
If you change the "umask=007" option to "umask=000" and remount the drive then everything on the drive should be read/writable by every user on the system.

If you want to restrict access to a particular user, you can use uid= and gid= like so:

```

/dev/sdb1 /media/disk ntfs defaults,uid=1000,gid=1000,umask=007,noatime 0 0

```

That will make everything on the drive read/write/executable for the user with UID 1000 and everybody in the group with GID 1000.

---

### Post by RiTarDid on 2008-09-11
Thanks, that clarifies things wonderfully :)

---

