---
title: "SanDisk &quot;Ultra Backup&quot; -how to disable write protect"
date: 2010-03-27
forum: Hardware
---

### Post by George Heine on 2010-03-27
Working with an 8GB SanDisk "Ultra Backup" flash drive. 
When inserted, Ubuntu performs two automounts.  

The first is a 7.9+ GB file system, which reads and writes like any other flash drive. 
(At least on Linux; it does some weird things on Windows, such as copy hidden files) 

The second is a 93 MB read-only file system which lshal recognizes as /dev/sr1 with a volume label "U3 System".  Trying to mount /dev/sr1 as rw causes an error.  Also, it does not seem to be possible to write to /dev/sr1 with low-level commands such as "dd" or "fdisk".  

I would like to erase that second file system and recapture that extra 93 mb of space, and, if possible, merge that extra space into the existing 7.9+ GB file system.

Is this second file system somehow hardware write-protected?  I didn't know that was
possible on a USB flash drive.  Is there any way to defeat the write protection?

thanks for any help -

---

### Post by xredan on 2010-03-27
there should be a little switch on the side of the usb flash drive to turn it off:P:p

---

