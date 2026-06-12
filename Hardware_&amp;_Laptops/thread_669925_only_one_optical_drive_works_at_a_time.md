---
title: "only one optical drive works at a time"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by mikeize on 2008-01-16
I have a cdrw drive and a dvdrw drive.  They both are recognized by ubuntu, but only one at a time will read a disc.  Actually, it's day to day (or boot to boot), that one drive or the other will/won't read a disc.  One is new and one is old.  I don't get it.  Ideas?

-mike

---

### Post by mikeize on 2008-01-17
Yes they both show up in ubuntu (ie, in "Computer").  I'll have to check bios and windows...

-mike

edit:  both drives work simultaneously in windows, and bios appears to recognize them both, as far as i can tell...  they are both listed in "boot order" screen, but on the "drives"? screen only the SATA drives are detailed (including the dvd drive).  I have one IDE hard drive (works fine), and the CD drive is IDE too.  IDE is set to "legacy" or something like that.

---

### Post by mikeize on 2008-01-17
Yes.  They both triggered a "what to do" box, and i successfully tested the music on each disc.

-mike

---

### Post by Yellow Pasque on 2008-01-17
Ok, so you put a disc in one drive and it auto-mounts and gives you an icon on your desktop? And then you put a disc in the other and it does nothing?

Can you run this for me?
```
lshw -businfo -C disk
```

Also, can you post your /etc/fstab file?
Thanks.

---

### Post by mikeize on 2008-01-17
Somewhere along the line I told ubuntu not to show drives on the desktop.  I do know that when one drive is "working", the icon in "Computer" will say "audio disc" or something like that.  If the drive is not "working" then the icon will not change from "cdrw" or whatever kind of drive it is.  Here is the info you requested.  Thanks for your help.

-mike

```
mike@u-desktop:~$ sudo lshw -businfo -C disk
[sudo] password for mike:
Bus info          Device       Class          Description
=========================================================
scsi@4:0.0.0      /dev/cdrom1  disk           CD-RW CRW4850
                  /dev/cdrom1  disk           
scsi@4:0.1.0      /dev/sdc     disk           189GB Maxtor 6L200R0
scsi@0:0.0.0      /dev/cdrom   disk           DVDRW LH-20A1L
                  /dev/cdrom   disk           
scsi@1:0.0.0      /dev/sda     disk           298GB WDC WD3200AAKS-0
scsi@2:0.0.0      /dev/sdb     disk           698GB WDC WD7500AAKS-2

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bbde088a-ff6e-48b6-ac79-3c36d3bee9b9 /               reiserfs notail          0       1
# /dev/sda3
UUID=a0676ca3-b896-4299-a383-681fa7eccd66 /home           ext3    defaults        0       2
# /dev/sda1
UUID=F43CD8D93CD89846 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=598f964c-f1d9-4c37-aed2-7574fa9f9306 /media/storage     ext3    defaults	  0	  2
# /dev/sdb2
UUID=59B5E97F73A47917 /media/xp-storage	  ntfs	  defaults	  0	  2
# /dev/sdc1
UUID=1E8312CB17BD09AE /media/sdc1     ntfs    defaults        0       2
# /dev/sdc2
UUID=5E54E9A97C04437B /media/sdc2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=5eb6a222-d273-472b-9eef-10a79e469611 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by Yellow Pasque on 2008-01-17
Maybe you should try this advice from the HAL (Hardware Abstraction Layer) wiki:
> Inserted CD/DVD are not recognized by hal
If inserted CDs/DVDs are not recognized by hal (no icon on the desktop), check the /etc/fstab and remove the lines for the optical drives. 
Instead of deleting the lines, just comment them out with a '#' so you can easily restore them if you want to.

---

### Post by mikeize on 2008-01-17
Okay, I commented them out and I'll reboot in a minute.  The funny thing is that right now, they both appear to be working (each has a disc and each says so), but no matter which one I double-click, it brings up the SAME album!  They are 2 different discs, but it's as if ubuntu thinks they are the same.  It really seems like a weird mount problem.  Anyway, rebooting now.

-mike

---

### Post by Yellow Pasque on 2008-01-17
Ok, I should've had you run just: lshw -C disk
That should list all the shortcuts for each drive.

---

### Post by mikeize on 2008-01-17
After reboot, same problem.  Whichever disc is in the DVD drive, will show up in both drives, but only if there is *a* disc in the CD drive too.  So ubuntu knows if there is a disc physically in the CD drive or not, but when clicked, it reads from the DVD drive!

-mike

```
mike@u-desktop:~$ sudo lshw -C disk
[sudo] password for mike:
  *-cdrom                 
       description: CD-R/CD-RW writer
       product: CD-RW CRW4850
       vendor: AOPEN
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.04
       serial: [AOPEN   CD-RW CRW4850   1.040
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom1
  *-disk
       description: SCSI Disk
       product: Maxtor 6L200R0
       vendor: ATA
       physical id: 0.1.0
       bus info: scsi@4:0.1.0
       logical name: /dev/sdc
       version: BAJ4
       serial: L50YR3LG
       size: 189GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-cdrom
       description: DVD-RAM writer
       product: DVDRW LH-20A1L
       vendor: LITE-ON
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: BL02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: SCSI Disk
       product: WDC WD3200AAKS-0
       vendor: ATA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 12.0
       serial: WD-WCARW0309510
       size: 298GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk
       description: SCSI Disk
       product: WDC WD7500AAKS-2
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 30.0
       serial: WD-WCAPT0449367
       size: 698GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
mike@u-desktop:~$ 

```

---

### Post by Yellow Pasque on 2008-01-17
Ok, I'm trying to figure out where the issue is, if it's with GNOME or something deeper. Put a CD in both drives and try accessing looking at their contents in a terminal (cd /media and see what cdrom directories are there and what they contain).

---

### Post by mikeize on 2008-01-17
Here you go.  It seems like it doesn't recognize the CD drive.

```
mike@u-desktop:/media$ dir
cdrom   cdrom1  floppy0  sdb1  sdc1  storage   xp-storage
cdrom0  floppy  sda1     sdb2  sdc2  wine-iso
mike@u-desktop:/media$ cd /media/cdrom
mike@u-desktop:/media/cdrom$ dir
mike@u-desktop:/media/cdrom$ cd media/cdrom1
bash: cd: media/cdrom1: No such file or directory

```

---

### Post by Yellow Pasque on 2008-01-17
and what about cdrom0? (Note: YOu did use non-blank CD's, right?)

---

### Post by mikeize on 2008-01-17
Sorry, and yes, both cd's contain music and both work in the DVD drive.

```
mike@u-desktop:~$ cd /media/cdrom0
mike@u-desktop:/media/cdrom0$ dir
mike@u-desktop:/media/cdrom0$ 
```

---

### Post by mikeize on 2008-01-17
sorry but I've got to go to work now.  I'll be checking back in, in about 4 hours or so.  Thanks for your help.

-mike

*edit* back now!

---

### Post by mikeize on 2008-01-19
still looking for a solution...

---

### Post by mikeize on 2008-01-26
I still haven't figured this out yet, so I'm just giving another bump to the thread!  Thanks.
I don't know if this is significant or not, but VLC has the drives backwards...  if I click file>open disc, the dvd defaults are set to dev/scd1, and the cd/vcd defaults are dev/scd0.  I have to manually change the 1 to a 0 if I want to watch a dvd.

-mike

---

### Post by mikeize on 2008-02-08
hate to bump this, but surely someone can help me?

-mike

---

