---
title: "Auto-mount hard drives"
date: 2009-03-22
forum: Hardware
---

### Post by Brandon! on 2009-03-22
I'm trying to setup my /etc/fstab to automatically mount my two slave hard drives when I boot up Ubuntu.  Right now, I can go to Places > [Hard drive] and it mounts no problem.  I tried running through the [InstallingANewHardDrive help page]("https://help.ubuntu.com/community/InstallingANewHardDrive"), but whenever I edit my fstab, I get the following error:
```
[ 1944.718727] VFS: Can't find ext3 filesystem on dev sda.
```

Just for reference, here's my sudo lshw -C disk
```
  *-disk                  
       description: ATA Disk
       product: WDC WD4000KD-00N
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WMAMY1115639
       size: 372GiB (400GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=531190f8
  *-cdrom:0
       description: CD-R/CD-RW writer
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw
       configuration: status=nodisc
  *-cdrom:1
       description: DVD writer
       product: DVD_RW ND-3520A
       vendor: _NEC
       physical id: 1
       bus info: scsi@2:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.04
       serial: [_NEC    DVD_RW ND-3520A 1.0404112400
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: ATA Disk
       product: WDC WD800JB-00JJ
       vendor: Western Digital
       physical id: 2
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 05.0
       serial: WD-WCAM9T975704
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000ccfbb
  *-disk:1
       description: ATA Disk
       product: WDC WD1200JB-00E
       vendor: Western Digital
       physical id: 3
       bus info: scsi@3:0.1.0
       logical name: /dev/sdc
       version: 15.0
       serial: WD-WMAEK1379774
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0b6665ab
```
I'm trying to mount *-disk and *-disk:1 which were formatted in Windows XP.  Any input would be amazing.

EDIT: Here's the line I'm adding to fstab:
```
/dev/sda    /media/Big_Boy   ext3    defaults     0        2
```

Thanks,

---

### Post by ktmom on 2009-03-23
[This thread]("http://ubuntuforums.org/showthread.php?t=785263&highlight=edit+fstab") helped me.  I didn't know if you had seen it.

---

### Post by Brandon! on 2009-03-26
Thank you, thank you, thank you.  I didn't see that thread before (or that forum even), but the tip worked.  I had a small problem with one of my drives not mounting because the /media/* directory already existed.  I'm not sure why it was like that, but I was able to delete it, reboot and then everything started to work.

[rant]Unfortunately, stuff like this is why I get frustrated learning Ubuntu.  Once you know what program to install, everything is flawless.  Finding that program or knowing that one even exists is what sucks... For a feature like this, why not include it by default?[/rant]

---

### Post by sahabcse on 2009-03-26
Hi

Please follow below url for mounting ntfs/fat32 parttions.

[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

