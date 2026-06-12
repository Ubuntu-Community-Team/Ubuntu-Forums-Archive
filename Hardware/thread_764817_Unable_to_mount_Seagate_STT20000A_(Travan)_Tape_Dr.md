---
title: "Unable to mount Seagate STT20000A (Travan) Tape Drive"
date: 2008-04-24
forum: Hardware
---

### Post by rkulp on 2008-04-24
I have been unable to mount a tape on my Seagate STT20000A tape drive. I am running Hardy Heron on an old Pentium III Gateway. Here is (I hope) the relevant information from dmesg:

[   39.415515] ata2.00: ATAPI: SAMSUNG CD-R/RW DRIVE SW-252F, R801, max UDMA/33
[   39.415574] ata2.01: ATAPI: Seagate STT20000A, 8A51, max MWDMA2
[   39.415597] ata2.01: device is on DMA blacklist, disabling DMA
[   39.579435] ata2.00: configured for UDMA/33
[   39.751291] ata2.01: configured for PIO4
[   39.751647] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-00AU 18.2 PQ: 0 ANSI: 5
[   39.751971] scsi 0:0:1:0: Direct-Access     ATA      WDC WD400BB-75AU 18.2 PQ: 0 ANSI: 5
[   39.753599] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-252F  R801 PQ: 0 ANSI: 5
[   39.758122] scsi 1:0:1:0: Sequential-Access Seagate  STT20000A        8A51 PQ: 0 ANSI: 2
[   40.946151] Driver 'sd' needs updating - please use bus_type methods
[   40.946763] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   40.946807] sd 0:0:0:0: [sda] Write Protect is off
[   40.946816] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   40.946878] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.947023] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   40.947058] sd 0:0:0:0: [sda] Write Protect is off
[   40.947066] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   40.947124] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.947138]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   40.974017] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   40.974077] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[   40.974140] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   40.974195] scsi 1:0:1:0: Attached scsi generic sg3 type 1
[   40.983699]  sda5 >
[   40.984000] sd 0:0:0:0: [sda] Attached SCSI disk
[   40.984204] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   40.984247] sd 0:0:1:0: [sdb] Write Protect is off
[   40.984256] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   40.984318] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.984446] sd 0:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   40.984481] sd 0:0:1:0: [sdb] Write Protect is off
[   40.984489] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   40.984549] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.984562]  sdb: sdb1
[   40.993562] sd 0:0:1:0: [sdb] Attached SCSI disk
[   41.026621] sr0: scsi3-mmc drive: 52x/1x writer cd/rw xa/form2 cdda tray
[   41.026635] Uniform CD-ROM driver Revision: 3.20
[   41.026763] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   41.132407] osst :I: Tape driver with OnStream support version 0.99.4
[   41.132415] osst :I: $Id: osst.c,v 1.73 2005/01/01 21:13:34 wriede Exp $
[   41.132498] Driver 'osst' needs updating - please use bus_type methods
[   41.194630] st: Version 20070203, fixed bufsize 32768, s/g segs 256
[   41.194712] Driver 'st' needs updating - please use bus_type methods
[   41.195134] st 1:0:1:0: Attached scsi tape st0
[   41.195143] st 1:0:1:0: st0: try direct i/o: yes (alignment 512 B)


If I understand this properly, the drive is assigned to /dev/st0. Here is the response when trying to find its status:

dick@Dick-Ubuntu:~$ mt -f /dev/st0 status
mt: /dev/st0: rmtopen failed: Input/output error

Here is the result of trying to mount the drive using KDat:


There appears to be no tape in the drive /dev/st0. Please check "Edit>Preferences" to make sure the correct device is selected as the tape drive (e.g. /dev/st0). If you hear the tape drive moving, wait until it stops and then try mounting it again.

I have tried all the suggestions I can find here or on other forums to no avail. Has anyone ever gotten this drive to work?

---

### Post by pyrotherm on 2008-05-07
I am fairly new to using tape drives with linux, but go ahead and try this

```
dick@Dick-Ubuntu:~$ mt -f /dev/nst0 status
```

notice the "n" in there?

It has been explained to me that you will get undesired results using st0

Hope this helps!

---

### Post by hubiedo on 2008-06-20
i am having the same trouble with the st20000 tape drive. any help would be appreciated.

i am able to use mt -f /dev/st0 erase or retension and status but kdat says there is no tape.

hubie

---

### Post by Odrodzona-Sarmacja on 2008-06-21
I don't know even there was something like tape drive on Linux, but...
"sudo blkid"
"mount"
I would be using to check if device is detected by Linux and if it is mounted somewhere already. I hope it helps some.

---

### Post by ronnieredd on 2008-07-11
I'm not completely finished with working this out on one of our DL 380 G4 servers, however if you want to jump start your drive not getting recognized, this is what I am doing - so far.
Background:
Trying to turn a **HP DL 380 G4** server into an Ubuntu 8.04.1 Bacula backup machine. The drive is an **HP MSL2024** library.
What I've done so far:
First try to see with :
```
# lsscsi
```
Mine looked something like this:
# lsscsi
[0:0:0:0] * *cd/dvd *TEAC * * DW-224E-B * * * *C.6F */dev/scd0

```
# modprobe st
```

If you get any error messages - stop. That should get fixed first.
Otherwise -
Do the following :

```
# echo "engage scsi" > /proc/driver/cciss/cciss0
```
```
# echo "rescan" > /proc/driver/cciss/cciss0
```

Check dmesg again

```
# dmesg
```
Verify that you should have /dev/st0 and /dev/tape hardlink-ed to it
(Should have automatically created for you )

Put the above 2 echo command to the /etc/rc.local so that it will be executed 
everytime the system start.[/list]

The above can be applied to any tape drives connected to the Smart Array 5i 
(cciss).

lssci shows the tape drive now.
```
# lsscsi
```
[0:0:0:0] * *cd/dvd *TEAC * * DW-224E-B * * * *C.6F */dev/scd0
[2:0:0:0] * *tape * *HP * * * Ultrium 4-SCSI * B34W */dev/st0

This may or may not help. At least I can see the drive. I also installed everything I could find via synaptics/apt-get that had to do with hp, scsi and tape backups.

Once I get everything to work as planned, I'll post a link to documentation.
If anyone else can input some help here, it would be greatly appreciated.

---

### Post by voodoobettie on 2008-08-19
I followed the advice above to mount my HP Ultrium tape drive and it all worked for me except the echo commands. Now I can see my tape drive when I run lsscsi.

Thanks!

:guitar:

---

### Post by fromgi on 2008-10-27
I just install Mandriva 2009 Gnome.  A backup utility is installed which recognized my Seagate STT20000A tape drive.  This is the first time I was able to access my tape drive after leaving windows!

Mandriva also recognized my ATI graphics card.  I didn't have to use the safe graphics mode either!

I'll probably make the switch from Ubuntu!

---

