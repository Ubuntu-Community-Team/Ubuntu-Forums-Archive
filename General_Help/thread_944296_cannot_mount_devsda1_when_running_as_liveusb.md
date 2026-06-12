---
title: "cannot mount /dev/sda1 when running as liveusb"
date: 2008-10-11
forum: General Help
---

### Post by debernardis on 2008-10-11
After some searching, it doesn't seem this has been covered in these forums. So here's my question:

I have ubuntu 8.04.1 liveusb running nicely from several machines I've access to. My problem is, I can't mount the first partition of these machines' hard disks, namely /dev/sda1, which is tipically a ntfs partition hosting some flavour of the windows os.

Whenever I try, I get an error message that says, more or less:

"mount: according to mtab, /dev/sda1 is already mounted on /media/disk-1"

(the mount point may change according to the partition name).

I can't see the contents of /etc/mtab because when I do cat /etc/mtab I get 

cat: /etc/mtab: I/O error

I guess this is something coming from the unionfs, maybe? Is there a way I can circumvent this problem? I need to reach those ntfs partitions to scan them with clamav and f-prot :-)

Thanks for your help.

EDIT: I forgot to tell that when /dev/sda1 is ext3 I have no problems.

EDIT: solved. My casper-rw partition was borked. I have recreated it and now ntfs partitions are again mountable.

---

