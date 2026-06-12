---
title: "help: the dvd driver doesn't load anything anymore!"
date: 2011-12-13
forum: Hardware
---

### Post by ubunlilluz on 2011-12-13
Hi,
well i've this problem from yesterday: my cd/dvd driver doesn't load any cd/dvd. I've tried with original cd/dvd but nothing, it tries to load it, i hear that it is working,  but then nothing happens.
Then if i try to mount manually i get:
```
drlillux@domuslillux:~$ sudo mount /dev/sr0 
mount: no medium found on /dev/sr0
```
Everything started when i was trying to install Windows seven on Virtualbox, but i don't think that virtualbox could change system configuration. 
Then i put other information:
```
drlillux@domuslillux:~$ dmesg | grep CD-ROM
[    3.242133] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22LS50  TL02 PQ: 0 ANSI: 5
[    3.248287] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.248432] sr 6:0:0:0: Attached scsi CD-ROM sr0
```

And my fstab is:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_beefbehdgi_Domusraid1 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_beefbehdgi_Domusraid3 /home           ext4    defaults        0       2
/dev/mapper/isw_beefbehdgi_Domusraid2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sr0     /media/cdrom0   udf,iso9660 user,rw,noauto,exec,utf8 0       0

```

How can i solve this problem? 
Thanks

---

