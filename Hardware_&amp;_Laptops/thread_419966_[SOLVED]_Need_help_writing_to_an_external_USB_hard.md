---
title: "[SOLVED] Need help writing to an external USB hard drive"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by bswilson on 2007-04-23
Friends,

I have an external USB 2.0 *Maxtor *hard drive (100GB) that is mounted to by Ubuntu 7.04 system.  I recently upgraded from 6.10.  Sadly, my drive doesn't seem to be working as well as it used to.

I use **cron** to call a shell script I wrote that basically uses **rsync** to keep my home directory backed up.  This worked beautifully on 6.10, but now that I've upgraded I get all these **rsync** errors when I invoke the script.  My *Maxtor *drive seems to be mounted in a different way; I can't figure out what to do.  

Basically, **rsync** won't back up many files because of write and ownership permissions on this USB drive.  Granted, I have it mounted as vfat (and FAT32 doesn't store or support ownership changes).  Is there anything I can do to fix this?

Here is some select output:

```
$ mount
/dev/sda5 on /media/BACKUP type vfat (rw,nosuid,nodev,iocharset=utf8,umask=000)

$ ls -alF |grep BACKUP
drwxrwxrwx 11 root     root     32768 2007-04-23 11:01 BACKUP/
```

---

### Post by bswilson on 2007-04-23
Well, I think I came across the solution.  I had been modifying my **/etc/fstab** file in order to allow the current user to mount the file.  But I invoked the **mount -a** command as **sudo mount -a**, which meant it got mounted as root!  I rebooted and as it turns out, my **fstab** file allowed **pmount** to attack my USB drive, but as the current desktop user (me).

My **/etc/fstab**:

```
$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda5       /media/BACKUP   vfat    iocharset=utf8,rw,user,exec,umask=000   0       0
```

---

