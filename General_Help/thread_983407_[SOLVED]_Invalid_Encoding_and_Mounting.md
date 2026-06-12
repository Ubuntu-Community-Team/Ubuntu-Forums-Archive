---
title: "[SOLVED] Invalid Encoding and Mounting"
date: 2008-11-15
forum: General Help
---

### Post by rabid9797 on 2008-11-15
Im having some problems with filenames. In files and folders that use special characters, i get an (invalid encoding) error in the filename/folder when i view them from my laptop. The files are on my desktop and i have the drive mounted through cifs. On my desktop though, the files and folders don't have the same problem with encoding.

So, what im thinking(after some research) is that i need to force the drive to mount with another character encoding scheme in fstab, i just don't know how to do that. 

Can anybody help me out? Below i've included my fstab contents, and the attached picture is of my problem(two views of folders with the invalid encoding)

Thanks

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=7f0b1ca2-d0b3-4bd4-b3cd-83ade8dd70ed /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=cf9cfe23-96a0-4383-9448-c0f98a0d669f /home           ext3    relatime        0       2
# /dev/sda3
UUID=082661bd-e06d-4079-a0ff-c9432379996a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
#This is my remote drive
\\192.168.1.138\floyd /media/remote cifs user,exec 0 0

```

---

### Post by rabid9797 on 2008-11-17
EDIT:

I found another thread, and thanks to dcstar, i was able to fix my problem.

Here is the bug: [https://bugs.launchpad.net/ubuntu/+bug/200595](https://bugs.launchpad.net/ubuntu/+bug/200595)

i had to add 
```
iocharset=utf8
```
into the options on my drive to fix the problem. 

Just thought i'd post my answer for future searchers.

---

