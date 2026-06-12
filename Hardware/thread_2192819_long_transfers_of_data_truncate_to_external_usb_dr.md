---
title: "long transfers of data truncate to external usb drive"
date: 2013-12-09
forum: Hardware
---

### Post by codenine75a on 2013-12-09
I am getting truncated transfers of data to my external usb drive.  I did not have this in ubuntu so I'll just use xubuntu then.

---

### Post by Bashing-om on 2013-12-09
codenine75a;

Is the external usb drive formatted fat32 ?
If this is a FAT32 filesystem, there is a 4GB limit on files being stored. You'll need to reformat to NTFS.
[http://support.microsoft.com/kb/314463](http://support.microsoft.com/kb/314463)
> 
You cannot create a file larger than (2^32)-1 bytes (this is one byte less than 4 GB) on a FAT32 partition.


[INDENT]some limits do apply
[/INDENT]

---

