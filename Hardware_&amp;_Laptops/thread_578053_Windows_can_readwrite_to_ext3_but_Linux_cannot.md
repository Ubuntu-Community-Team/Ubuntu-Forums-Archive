---
title: "Windows can read/write to ext3 but Linux cannot"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by checho4 on 2007-10-16
Hi, I have an uncommon problem.  I installed a program called Ext2IFS to read my ext3 partition on Windows.  This is a partition I set out solely for Music.  Everything was alright for a while, but about 2 months ago, Linux totally stopped reading my music partition.  Windows has full access to it, but Linux does not.  I don't understand what could possibly be wrong!  Is there any way to fix this problem?  I really love Amarok and hate having to go into Windows to listen to music.  Any help is greatly appreciated!

---

### Post by aysiu on 2007-10-16
Can you paste these two commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and the paste the output back here? ```
sudo fdisk -l
df -h
```

---

### Post by checho4 on 2007-10-17
sudo fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        3219    25776292+   7  HPFS/NTFS
/dev/sda3            3220       14593    91361655    5  Extended
/dev/sda5            3220        7061    30860833+  83  Linux
/dev/sda6            7527       14593    56765646   83  Linux
/dev/sda7            7062        7526     3735081   82  Linux swap / Solaris


df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              29G  6.2G   22G  23% /
varrun                439M  232K  438M   1% /var/run
varlock               439M     0  439M   0% /var/lock
procbususb            439M  120K  438M   1% /proc/bus/usb
udev                  439M  120K  438M   1% /dev
devshm                439M     0  439M   0% /dev/shm
lrm                   439M   39M  401M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1              79M  7.7M   71M  10% /media/sda1
/dev/sda2              25G   15G   11G  60% /media/sda2

---

### Post by aysiu on 2007-10-17
Is /dev/sda6 your music partition? Because it isn't mounted.

Can you post the output of this command as well? ```
cat /etc/fstab
```

---

### Post by checho4 on 2007-10-17
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=6857693d-ed9e-4230-8e45-312c517f354f / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=07D7-051C /media/sda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=AE74D88E74D85AA3 /media/sda2 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda6
# /dev/sda7
UUID=df41b107-a682-44f4-ae02-13ccc104c41f none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda6 /media/Music ext3 users,atime,noauto,rw,nodev,noexec,nosuid 0 0




How do I mount my Music partition?

---

### Post by aysiu on 2007-10-17
Based on this line: ```
/dev/sda6 /media/Music ext3 users,atime,noauto,rw,nodev,noexec,nosuid 0 0
``` it appears that it should be mounted already, but it isn't mounted. Try this: ```
sudo mkdir /media/Music
``` (if you're told the directory already exists, that's okay--just proceed to the next command): ```
sudo mount -t ext3 /dev/sda6 /media/Music
cd /media/Music
ls
``` If you get any other error messages, please post them back here.

---

### Post by checho4 on 2007-10-17
Here is EXACTLY what just happened:

user@localhost:~$ sudo mkdir /media/Music
Password:
mkdir: cannot create directory `/media/Music': File exists
user@localhost:~$ sudo mount -t ext3 /dev/sda6 /media/Music
user@localhost:~$ cd /media/Music
user@localhost:/media/Music$ ls
Segmentation fault
user@localhost:/media/Music$

That line right there: "Segmentation fault"  What does that mean?

---

### Post by aysiu on 2007-10-17
That's weird. I've never seen a segmentation fault when listing the contents of a folder.

[This search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+segmentation+fault&btnG=Google+Search) may help. I'm not sure if it will, though.

---

### Post by checho4 on 2007-10-17
I tried the "ls" command again and this time, the command is just hanging on me.  It isn't doing anything.  And I can't seem to find anything relating to my problem.  No one has gotten the error from checking their directory, and the few who are closely related seem to have been able to just restart their computer and it'd be all back.

Any other advice?

---

### Post by aysiu on 2007-10-17
It's possible Windows may have corrupted the Ext3 partition somehow.

---

### Post by atlfalcons866 on 2007-10-17
try 
sudo touch /forcefsck

then reboot then it will fsck the partition to see if its corrupted or not

---

### Post by checho4 on 2007-10-17
I'm guessing that's the case.  Is there any way to repair the partition without damaging my files?  I know I can access my music via Windows, but not all of it, so I'm hoping I can recover the music files.

Is there any way to repair a partition via linux?

---

### Post by Zamboniman on 2007-10-17
> **checho4 said:**
> I'm guessing that's the case.  Is there any way to repair the partition without damaging my files?  I know I can access my music via Windows, but not all of it, so I'm hoping I can recover the music files.

Is there any way to repair a partition via linux?

```
sudo e2fsck /dev/sda6
```

---

### Post by checho4 on 2007-10-18
I am currently backing up whatever files Windows can still read and will try these methods out later tonight.  I'll let you know how it goes...

---

### Post by checho4 on 2007-10-24
Sorry about the late reply.  My laptop had to be sent into Dell to replace the LCD screen.  However, I did try these methods and THEY WORKED!!!  THANK YOU SO MUCH!!!  Apparently, one of the files "lost+found" was missing.  Thank you!!!  My music is all safe!

---

### Post by hessiess on 2007-10-24
i have the win ext2/3 driver has a tendency to corrupt the partition, especially if windows is not shut down correctly

---

