---
title: "unable to mount DVDs"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by ksu_mustang on 2007-12-27
I am unable to mount DVDs.  I can mount CDs  (audio and data) just fine.  When I try to mount a DVD from the command line I get:
> 
**~$** sudo mount /dev/hda
mount: No medium found


I have tried mounting the DVD with types "udf", "iso9660", and "auto".
I have set the region code to "1" using the command "regionset /dev/hda"
I have tried 5 different DVDs. 

I have been struggling with this for over a month now, and have no ideal whats wrong.  I have searched google and Ubuntu Forums with no luck so far.  Please help me.

My machine:
    Ubuntu 7.10 (up to date)
    Kernel: 2.6.22-14-generic
    Tyan Tiger K8W (s2875)
    Dual AMD Operton 242
    1 GB Ram
    2 SATA Hard Drives
    Samsung DVD+-RW

> 
**~$** cat /etc/fstab
proc /proc proc defaults 0 0
# /dev/sda1
UUID=a1661d16-0011-469b-af5a-ac3bf7885189 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda3
/dev/sda3 /storage/a xfs nouser,atime,auto,rw,nodev,noexec,nosuid 0 0
# /dev/sda2
UUID=f54db839-7f88-45e6-bc02-f50267afbb52 none swap sw 0 0
/dev/sdb1 /storage/sdb xfs nouser,atime,auto,rw,nodev,noexec,nosuid 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

> 
**~$** sudo lshw -C disk
[...]
  *-cdrom
       description: DVD-RAM writer
       product: TSSTcorpCD/DVDW SH-S182M
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: SB02
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma2 status=nodisc


Thanks in advance ~

---

### Post by bjayeblue on 2008-01-19
hi there, i just fixed a similar issue on my machine..

is your box setup to play restricted format DVD's? if not, try the following Ubuntu doc..

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

i hope this helps

---

