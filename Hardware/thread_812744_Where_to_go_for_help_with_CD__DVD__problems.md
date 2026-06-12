---
title: "Where to go for help with CD / DVD  problems?"
date: 2008-05-30
forum: Hardware
---

### Post by AVH on 2008-05-30
Where is a good place to get help with CD or DVD mount and recognition problems? 

Most posts to this forum on these subjects seem to get no replies. Of the rest, most replies are just sympathy.

 Which is nice! But, doesn't solve the problem.

So... Is there someplace where a little more expertise is available?

Thanks
Alan

---

### Post by stream303 on 2008-05-30
What is the problem again?

One thing I have to be aware of when using older Apple PPC boxes is to use CD-R's instead of CD-RW's for iso install images, and making sure that if I burn a CD on another machine, that it isn't burned at too fast a speed for the older machines to handle.

Not sure if this might be part of the problem, but thought I'd throw this out there....

---

### Post by sneeks on 2008-05-30
do you have a specific problem mate??

---

### Post by AVH on 2008-06-01
I posted here a week ago and got no replies. 
[http://ubuntuforums.org/showthread.php?t=805438&highlight=dvd](http://ubuntuforums.org/showthread.php?t=805438&highlight=dvd)

 I searched through the forum for similar problems, hoping to find  a solution. Going back two or three weeks I found maybe fifteen or so requests for help with CD/DVD mounting or recognition problems and only two or three helpful responses. A majority of requests didn't get any response at all.

People on this forum are generally very helpful so my conclusion was that there just wasn't much help for this type of problem available here. Hence, my question.

---

### Post by AVH on 2008-06-09
Bump. So... no help and not even any advice on where to find Help?

---

### Post by mc4man on 2008-06-10
Probably in Multimedia and Graphics
For starters after a normal (no disk) boot run and post
```
sudo lshw -C disk 
```
Do it once with drive empty and then with a dvd inserted (wait for drive light to go steady, only post if different)
Wouldn't hurt to see ```
cat /etc/fstab
```and after above action ```
dmesg | tail
```

---

### Post by AVH on 2008-06-10
Thanks

sudo lshw -C disk with no disks in either cd/rom or dvd/rw

```
alan@alan-u-livingroom:~$ sudo lshw -C disk
[sudo] password for alan:
  *-cdrom                 
       description: SCSI CD-ROM
       product: CD-ROM XM-6202B
       vendor: TOSHIBA
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1108
       capabilities: removable audio
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: ST3160812AS
       vendor: ATA
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5LS2FHF6
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW SH-S203N
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
alan@alan-u-livingroom:~$ 
```

sudo lshw -C disk with in dvd/rw

```
alan@alan-u-livingroom:~$ sudo lshw -C disk
[sudo] password for alan:
  *-cdrom                 
       description: SCSI CD-ROM
       product: CD-ROM XM-6202B
       vendor: TOSHIBA
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1108
       capabilities: removable audio
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: ST3160812AS
       vendor: ATA
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5LS2FHF6
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW SH-S203N
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom
alan@alan-u-livingroom:~$ 
```

sudo lshw -C disk with disks in bothr cd/rom and dvd/rw just adds this to the end of the cd/rom (first) entry.

```
*-disc
          physical id: 0
          logical name: /dev/cdrom1
```


The results of cat /etc/fstab:

```
alan@alan-u-livingroom:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=d82635a7-e2cf-431e-b6e7-bf21a5fa669c / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=22C88020C87FF081 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=765c3632-c078-4421-8b33-204011f160d4 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0
alan@alan-u-livingroom:~$
``` 


The results of dmesg | tail:

```
alan@alan-u-livingroom:~$ dmesg | tail
[  478.210864] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  478.546651] ata4.00: configured for UDMA/33
[  478.546665] ata4: EH complete
[  478.547467] ata4.00: exception Emask 0x52 SAct 0x0 SErr 0xffffffff action 0x6
[  478.547476] ata4.00: cmd a0/00:00:00:00:20/00:00:00:00:00/a0 tag 0 cdb 0x0 data 0 
[  478.547478]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x52 (ATA bus error)
[  478.547490] ata4: hard resetting port
[  479.425438] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  479.761225] ata4.00: configured for UDMA/33
[  479.761244] ata4: EH complete
alan@alan-u-livingroom:~$
``` 

I wonder if this problem is caused by the cd/rom being an IDE drive and the dvd/rw being a SATA drive?

---

### Post by mc4man on 2008-06-10
> I wonder if this problem is caused by the cd/rom being an IDE drive and the dvd/rw being a SATA drive?  Probably, there have been and continue to be issues with sata dvd-rw drives.
While fstab isn't as important as it once was yours is wrong. at some point we'll  delete this line /dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0 and replace with these 2
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```
It would be good  to see from /etc/udev/rules.d - the contents of 70-persistent-cd rules before you change fstab (it's more of a factor than fstab)

Also which drive (cdrw or dvd-rw) is the one which you could boot from (live cd ect.)

An interesting thing to do would be _ck. and post the ...rules file_, then boot to the livecd, run sudo lshw -C disk, ck. the ...rules, fstab and cross compare the results of all to what it shows now. (if they're all the same then lets fix fstab, square up the...rules file if needed and maybe try below, if they're different then post)

Sometimes with a sata dvdrw doing this can help  (post 80)
[http://ubuntuforums.org/showthread.php?t=767449&page=8](http://ubuntuforums.org/showthread.php?t=767449&page=8)
Edit: 
the OP of the thread link above now reports while it fixed his dvd , his hdd performance went way downhill, probably not a good option dependent upon hardware config

---

### Post by AVH on 2008-06-11
The bios is still set to boot from the old cd/rom. I wasn't going totry changing that until I had the dvd/rw working properly.

here is the 70-Persistent-cd.rules file contents:

```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.

# CDDVDW_SH-S203N (pci-0000:00:05.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:05.0-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:05.0-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:05.0-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:05.0-scsi-1:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# CD-ROM_XM-6202B (pci-0000:00:02.5-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:02.5-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
```


The output for sudo lshw-C diskafter booting from the live cd is slightly different. The scsi bus order has changed, the cd/rom number is reversed, and dvd drive is 'dev/dvd1' instead of 'dev/dvd'

sudo lshw -C disk from live cd:

```
ubuntu@ubuntu:~$ sudo lshw -C disk
  *-cdrom                 
       description: SCSI CD-ROM
       product: CD-ROM XM-6202B
       vendor: TOSHIBA
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1108
       capabilities: removable audio
       configuration: ansiversion=5 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: SCSI Disk
       product: ST3160812AS
       vendor: ATA
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 5LS2FHF6
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW SH-S203N
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
ubuntu@ubuntu:~$ 
```

---

