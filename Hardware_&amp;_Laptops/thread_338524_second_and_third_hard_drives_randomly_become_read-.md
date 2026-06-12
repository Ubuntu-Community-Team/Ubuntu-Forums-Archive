---
title: "second and third hard drives randomly become read-only"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by Archon-XR47 on 2007-01-14
I'm not sure if this is the right place to put this post, but I've been experiencing a very strange problem with my hard drives.  I have edgy installed on a sata 160 gb drive and two additional sata drives (400GB each) for storage.  The problem is with my two 400GB storage drives.  Both are formatted ext3 and both mount normally on boot with read/write capabilities.  The odd thing is, if I try to write ~1GB or more to either drive, the copy process stops partway through and I get a "file system is read-only" error.  After getting this error, I can no longer write any amount of data to either drive, nor can I even create a new folder on either drive. Upon checking the permissions of the folders that the drives mount to (/media/secondary and /media/tertiary) they still report me as the owner with full read/write access.  The only way to restore write functionality is to umount -a and then remount.  My fstab is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=161da565-d3e2-4bfe-bc17-0195d91d0102 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fc2f4f90-61ad-44da-841c-c869fec742fb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdc1	/media/primary			ntfs	nls=utf8,umask=0222 0	0
/dev/sdb1	/media/secondary		ext3	defaults	0	0
/dev/sdd1	/media/tertiary			ext3	defaults	0	0


You can ignore the sdc1 entry, that is strictly for accessing the files on my windows drive.

Any suggestions?

---

### Post by Archon-XR47 on 2007-01-16
After a lot of searching through google I came across the solution.  Evidently this is a known, but extremely rare problem with the ext3 fs.  For some reason the journalling aspect of ext3 was causing the disk to become read-only.  I couldn't really find a good explaination of why this is happening, but the solution is to revert the drive to ext2 (ie disable the journalling.) The steps to reverting to ext2 can be found here: 
[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-filesystem-ext2-revert.html]("http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-filesystem-ext2-revert.html")

---

