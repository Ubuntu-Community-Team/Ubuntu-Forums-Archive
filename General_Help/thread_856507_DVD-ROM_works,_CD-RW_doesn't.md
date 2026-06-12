---
title: "DVD-ROM works, CD-RW doesn't"
date: 2008-07-11
forum: General Help
---

### Post by TheForkOfJustice on 2008-07-11
I've come across this error when trying to burn an iso with wodim.

wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device was not specified. Trying to find an appropriate drive...
Looking for a CD-R drive to store 690.88 MiB...
Using drive: /dev/scd0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'IDE-DVD '
Identification : 'ROM 16x         '
Revision       : 'HD08'
Device seems to be: Generic mmc2 DVD-ROM.
wodim: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.

I have 2 drives. Wodim looks for a CD-RW drive (I have one as the slave) but can't find it so it tries the DVD-ROM master with obvious failure.

Everything works fine in WinXP

I looked in my fstab and it mentions /dev/scd0 and /dev/scd1 (one for each drive) but only /dev/scd0 exists and that's the designation of my DVD-ROM.

This used to work when Hardy was freshly installed but it has since broke with an update.  Is there a fix?  Can I create a 'new' /dev/scd1?

---

### Post by nikgare on 2008-07-11
What's the output of **wodim -scanbus**

---

### Post by TheForkOfJustice on 2008-07-14
Here:

> 
scsibus3:
	3,0,0	300) 'IDE-DVD ' 'ROM 16x         ' 'HD08' Removable CD-ROM
	3,1,0	301) *
	3,2,0	302) *
	3,3,0	303) *
	3,4,0	304) *
	3,5,0	305) *
	3,6,0	306) *
	3,7,0	307) *


It only sees one of my drives. Just the master DVD-ROM and not my slave CD-RW.

---

### Post by nikgare on 2008-07-15
Do you have the master/slave settings right on your optical drives?
Do other programs in Ubuntu see the other drive?

---

### Post by TheForkOfJustice on 2008-07-15
> **nikgare said:**
> Do you have the master/slave settings right on your optical drives?
Do other programs in Ubuntu see the other drive?

The master slave settings are fine. It isn't a hardware issue.

Other programs _do not_ see the second drive.

---

### Post by mc4man on 2008-07-15
run
```
cat /etc/udev/rules.d/70-persistent-cd.rules
```
if your cdrw isn't listed there then it's not being detected at boot, if it is there then a solution of some type is possible.(on the Os side)

---

### Post by TheForkOfJustice on 2008-07-16
My output:

> 
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# CD-RRW_SW-248F (pci-0000:00:0f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
# ROM_16x (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"



I can see that both are being detected by the kernel and at boot at least.  The problem now is figuring out why the damn thing can't be detected by other software.

Perhaps I need to manually make a /dev/ entry for it?  I think /dev/MAKEDEV may help with that but I have no idea how to use it.

---

### Post by mc4man on 2008-07-17
sorry i was thinking about a couple of similar issues and threads and didn't think thru what I posted.
The listing only shows the had been detected at some point, not now.
run ```
sudo lshw -C disk
``` and we'll see

---

### Post by TheForkOfJustice on 2008-07-17
Result:

> 
  *-disk:0                
       description: ATA Disk
       product: Maxtor 6Y160P0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y42X0MGE
       size: 152GiB (163GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=07f99abc
  *-disk:1
       description: ATA Disk
       product: WDC WD2500JB-00G
       vendor: Western Digital
       physical id: 1
       bus info: scsi@2:0.1.0
       logical name: /dev/sdb
       version: 08.0
       serial: WD-WMAL72287923
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a9acb5b1
  *-cdrom:0
       description: DVD reader
       product: ROM 16x
       vendor: IDE-DVD
       physical id: 2
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HD08
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: CD-R/CD-RW writer
       physical id: 3
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio cd-r cd-rw
       configuration: status=ready
  *-disk:0
       description: SCSI Disk
       product: USB SD Reader
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: 1.00
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:1
       description: SCSI Disk
       product: USB CF Reader
       vendor: Generic
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdd
       version: 1.01
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:2
       description: SCSI Disk
       product: USB SM Reader
       vendor: Generic
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sde
       version: 1.02
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde
  *-disk:3
       description: SCSI Disk
       product: USB MS Reader
       vendor: Generic
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sdf
       version: 1.03
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdf


The info we want (I'm guessing) is:

> 
  *-cdrom:0
       description: DVD reader
       product: ROM 16x
       vendor: IDE-DVD
       physical id: 2
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HD08
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: CD-R/CD-RW writer
       physical id: 3
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio cd-r cd-rw
       configuration: status=ready


cdrom:0 is my DVD-ROM and there is no problem with that.
cdrom:1 is the CD-RW that is being 'detected' but apparently isn't usable for some reason.

**EDIT**

Don't ask me how but it seems to have recovered some functionality. Maybe it was because I left a CD in while booting, I don't know. In any case the /dev points exist now.

However...even though the drives can now be 'seen', the media is still invisible when inserted (same old problem I had in Gutsy)

I try to burn something and get this in wodim:

> 
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device was not specified. Trying to find an appropriate drive...
Looking for a CD-R drive to store 645.97 MiB...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
wodim: Cannot do inquiry for CD/DVD-Recorder.
Errno: 5 (Input/output error), test unit ready scsi sendcmd: fatal error
CDB:  00 00 00 00 00 00
cmd finished after 0.000s timeout 40s


---

### Post by mc4man on 2008-07-17
What do you get from this? ```
sudo hdparm -i /dev/scd1
```
Also when you ran the lshw what type of media was in the cdrw drive?
> configuration: status=ready What didn't show up is this, (from mine with blank cd or audio cd, a data cd would show filesystem and mount info)
 > configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
you should see *-medium  ect.  
plus your not showing - ansiversion (maybe that's because your not 'showing' any *-medium


> Warning: Cannot raise RLIMIT_MEMLOCK limits. Device was not specified There are tons of post here and in various lauchpad bugs where the  failed burn logs have that line, I'll post some links for you.
Maybe post your fstab

---

### Post by TheForkOfJustice on 2008-07-19
> 
What didn't show up is this, (from mine with blank cd or audio cd, a data cd would show filesystem and mount info)


> 
Also when you ran the lshw what type of media was in the cdrw drive?

Originally. just a blank CD. I just put a game DVD in the DVD-ROM and a game CD in my CD-RW and got this output with the lshw command:

> 
*-cdrom:0
       description: DVD reader
       product: ROM 16x
       vendor: IDE-DVD
       physical id: 2
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: HD08
       capabilities: removable audio dvd
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
  *-cdrom:1
       description: CD-R/CD-RW writer
       physical id: 3
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio cd-r cd-rw
       configuration: status=ready


As you can see, first drive is normal but the second is just oblivious to any inserted media irregardless of type. the 'status=ready' must mean that its operational and waiting for media. Sadly, it can't detect any :(.

```
sudo hdparm -i /dev/scd1
```

> /dev/scd1:
 HDIO_GET_IDENTITY failed: No message of desired type


> 
you should see *-medium  ect.  
plus your not showing - ansiversion (maybe that's because your not 'showing' any *-medium


Like I said, my CD-RW is just not detecting the media.  Any media. The DVD-ROM works fine with all media types it was built to detect.

> 
There are tons of post here and in various lauchpad bugs where the failed burn logs have that line, I'll post some links for you.
Maybe post your fstab


I've made a post in one in Launchpad.  Name is Allan MacKinnon (scroll down quite a bit).

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076)

My fstab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=43fe4faf-b3c5-4833-88db-96ee3db6d729 /               ext3    relatime,erro$
# /dev/sda8
UUID=37c324eb-f557-4ad8-9a9c-b4d2f9c46237 /home           ext3    relatime     $
# /dev/sda7
# UUID=7723a94d-2ba5-4149-9bd2-a853da861c2f /media/gutsy    ext3    relatime   $
# /dev/sda5
UUID=c682e650-60b0-4387-a4d6-f0f431084dca none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Nothing looks wrong with it.

---

