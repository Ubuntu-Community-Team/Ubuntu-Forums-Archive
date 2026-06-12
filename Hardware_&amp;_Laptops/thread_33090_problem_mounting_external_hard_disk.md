---
title: "problem mounting external hard disk"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by Anguilla on 2005-05-09
hello, I have a lacie firewire disk, and I made 4 partition with fdisk, 2 with a fat32 file system and one with a ext3 file system, now the problem is that:

at startup the disk is automounted, I think by hotplug, (maybe no, I'm a newbie.. ;-) ) so the problem is that, the 2 fat32 disks are writeable by the normal users and no problem but the others 2 are like root filesystems... I looked in **fstab** but I don't have no lines for sda disk because is automounted by ubuntu, so looking in **mtab** I get this:
[I]
/dev/sda1 /media/LACIE vfat rw,nosuid,nodev,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sda2 /media/ieee1394disk vfat rw,nosuid,nodev,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
/dev/sda5 /media/ieee1394disk-1 ext3 rw,nosuid,nodev 0 0
/dev/sda6 /media/ieee1394disk-2 ext3 rw,nosuid,nodev 0 0[/I]

where sda1 and 2 are fat32 disks... someone can help me??? ](*,)  ](*,)

---

### Post by sksbir on 2005-05-09
what did you get when looking in
/media/ieee1394disk-1
and
/media/ieee1394disk-2

??

---

### Post by Anguilla on 2005-05-09
Free space.. but I can write there only as root... 
in the others 2 (fat32, LACIE and ieee1394disk) I can create directory and files as normal user...
The problem is that ubuntu automounts the 4 partitions I don't know how to make it automounting the 2 ext3 disk as a normal user filesystem...

---

### Post by Anguilla on 2005-05-10
someone can help me?
Can some one say to me what is that automount the drive?? hotplug?? or something different... and how to config the automonting because in fstab I don't find any line that speaks about my sda drive....

---

### Post by Emerick on 2005-05-17
Seems you need to change the umask in /etc/fstab.
Try 022.

---

### Post by Anguilla on 2005-05-22
the problem is that I DON'T HAVE ANY LINE about sda disks in fstab! so I don't know why is mounted like that and how to change!
I think I have to change something in hotplug...

---

