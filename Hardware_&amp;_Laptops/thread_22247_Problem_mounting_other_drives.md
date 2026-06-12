---
title: "Problem mounting other drives"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by darknuala on 2005-03-26
I have a 300 gig hard drive that I want to use as a secondary drive.  I want to be able to read/write to it, under my user acct, but it says that only root has access.  I have read and re-read tutorials on how to do this, but nothing works.  Here is my /etc/fstab settings.  I would like to be able to read/write to hdd1.  Can somebody please help!

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/windows    ntfs    defaults,errors=remount-ro 0       1
/dev/hdd1       /mnt/data       ext3    defaults,errors=remount-ro 0       1

---

### Post by alastair on 2005-03-26
Is it mounted?

Try :

sudo chown <your username>.<your group> /mnt/data
sudo chmod 755 /mnt/data

Then test you can write :

touch /mnt/data/TTT

---

### Post by jessenaiman on 2005-04-14
I also have a secondary hard drive I am unable to read. When I tried to mount the drive the system informed me it was already mounted. When I logged in through root it was still not visible. I searched the file system, if my hdb is mounted somewhen I have no clue. A walkthrough is needed in the ubuntu help files for this issue, and I'll write it if someone gives me the answer.

---

### Post by alastair on 2005-04-14
Mounted filesystems are stored in /etc/mtab (and /proc/mounts).

To diagnose :

Relevant messages from boot up in /var/log/syslog

i.e. probe/discovery of IDE/SATA/SCSI disks.

fdisk -l /dev/<drive>   (for whatever problem drive e.g. hdb, sda etc.)

/etc/fstab

---

### Post by jessenaiman on 2005-04-14
This is techonobable to me. I need a way to simply mount and be able to access my secondary drive. I cannot use Ubuntu unless it can do this, it's driving me crazy. I just tried kubuntu, which recognized the drive but refused to mount it. I had such high hopes for hoary. I could do this in the previous ubuntu. Ahhhhhhh. Help

---

### Post by MarkA on 2005-04-23
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

Try this link. It will show you how to mount your drive. I also found out how to mount a second drive on my Promise controller by just making the drive /media /sdc1 with the same arguments. I just had to sudo konqueror and create the directory /media/sdc1. This works. Just reboot.

Mark

---

