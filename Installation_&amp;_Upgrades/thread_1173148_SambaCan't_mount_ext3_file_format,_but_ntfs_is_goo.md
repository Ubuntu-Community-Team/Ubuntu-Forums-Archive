---
title: "Samba:Can't mount ext3 file format, but ntfs is good"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by musta78 on 2009-05-29
Ok.  So I have done this easy home file server from this thread. [http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

I know that they say in the beginning that you need ntfs file format.

The thing is.  The harddrive I've installed Ubuntu server 8.04.2 is divided into 2 partions.  It's the other partion I have trouble getting to when browsing in windows.  I have mounted another harddrive wich has ntfs, and it works fine.

I can see both drives when browsing, but the content is the same on both!

I've added two lines in fstab:
/dev/sda1 /media/store ext3 defaults 0 0
/dev/sdb1 /media/store ntfs defaults 0 0

Is there anything I can do so it works with ext3 also?

---

### Post by musta78 on 2009-05-29
This is all my harddrives, and it is sda1 I have trouble with.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       86369   693758961   83  Linux
/dev/sda2           90920       91201     2265165    5  Extended
/dev/sda3   *       86370       90919    36547875   83  Linux
/dev/sda5           90920       91201     2265133+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa676580a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    7  HPFS/NTFS

---

### Post by musta78 on 2009-05-29
This is my setting in /etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=74c19fd1-bf4c-4ab0-8f14-f0e87f021b7a /               ext3    relatime,erro$
# /dev/sda5
UUID=fa607474-88a2-451b-b85f-93a2df2eb088 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1 /media/store ext3 defaults 0 0
/dev/sdb1 /media/store ntfs defaults 0 0

---

### Post by musta78 on 2009-05-29
Solved:

The important part is that every harddrive must be mounted in a different folder. 

So what I needed to change was /media/store on sdb1 to media/store2

Easy when you know what to do

---

