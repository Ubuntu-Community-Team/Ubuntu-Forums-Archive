---
title: "Hard Drive refused uid 1000 (Kubuntu 7.10)"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by Indefual on 2007-10-20
Hello.

I just upgraded to Kubuntu 7.10--fresh install.  My second hard drive (sdb1) is giving me a "hal-storage-fixed-mount refused uid 1000" whenever I try to look at it.

I'm almost certain it's an ext3 with journalling.  It worked fine this morning in Ubuntu 7.04.

From [http://ubuntuforums.org/archive/index.php/t-473511.html](http://ubuntuforums.org/archive/index.php/t-473511.html) I tried to do some of that, but hit a wall with the cfdisk command.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a75461a1-bb53-480e-a3dc-c81fbc9994bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fc5f8662-d586-4e82-b18e-ff3461673ca5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

So, doing a cfdisk gives me "FATAL ERROR: Cannot open disk drive" when I type "cfdisk /dev/sda" (despite the fact that I'm using it!) or "cfdisk /dev/sdb" or if I add any partition numbers to it.

So, it's not trying to automount sdb1, but I can't get any information on sdb at all using cfdisk.  So is something massively wrong?  Any ideas on what else I should google, or what I should do to solve this issue?

Everyone else with this error seems to be using NTFS files systems.

---

### Post by Indefual on 2007-10-20
**UPDATE**
I just booted off of Ubuntu 7.04, and it can see the files just fine.  I then booted off of Kubuntu 7.04 and it gives the same error.  Both Live CDs.  Also, the Kubuntu 7.10 Live CD couldn't see it before I installed.  I hoped this problem would clear itself up.

So all versions of Kubuntu have trouble, but the version of Ubuntu seems to see and mount it just fine.

---

### Post by Indefual on 2007-10-20
**UPDATE**
I tried to reinstall Kubuntu 7.10.  This time I selected manual partitioning, and set mount points for the second hard drive.  It now seems to work fine.

---

### Post by Indefual on 2007-10-20
**UPDATE**
I tried to reinstall Kubuntu 7.10.  This time I selected manual partitioning, and set mount points for the second hard drive.  It now seems to work fine.

---

### Post by Dragon Man on 2008-02-12
I recently installed Kubuntu 7.10 as well and recieved the same error, however, with the help of a friend of mine, we've found a simple solution.

First, mkdir /mnt/yourdevicehere
Then, sudo mount -t yourfilesystemhere /dev/devicehere /mnt/devicehere -o uid=777

This is only advised if you only plan on having one account, as it grants read/write/execute access to all users, but it works quite well. To check, merely ls /mnt/devicehere  If you see the files in the root of your device, it's worked!

Enjoy!

---

