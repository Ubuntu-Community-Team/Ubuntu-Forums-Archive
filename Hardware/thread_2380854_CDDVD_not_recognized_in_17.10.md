---
title: "CD/DVD not recognized in 17.10"
date: 2017-11-20
forum: Hardware
---

### Post by a-web on 2017-11-20
I have been using a ZaReason (zareason.com) laptop for going on 7 years (!) with no big problems.  About a year ago I got a different primary computer and did a complete reinstall of ubuntu on the ZaReason machine (there were some power issues which the reinstall fixed).  Since that reinstall I have not used the CD/DVD drive, as everything seems to be on USB now.  But today I was trying to play a CD (or DVD), but nothing happens when I insert the disc.  I can't find the CD through a media player or /media.

Before the reinstall there was no problem with CD/DVD playing.  I'm currently running 17.10 and have reinstalled the restricted extras.  I'm still a noob on linux, though I can follow instructions and happy to post more information as needed.  Any help is appreciated!

---

### Post by a-web on 2017-11-21
Just did a fresh install of 17.10 but alas, no change.

---

### Post by a-web on 2017-12-22
There have been no views of this thread?  Now I feel like I'm talking to myself...

---

### Post by egeezer on 2017-12-22
There have been issues reported for 17.10 on Lenovo laptops and some other machines.  The first report was from Phoronix, but do search for other sources. Link: [https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.10-BIOS-Corrupter](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.10-BIOS-Corrupter)

---

### Post by DuckHook on 2017-12-22
I doubt the OP is still monitoring this oldish thread. In any case, the linked problem, which is locked BIOS and unbootable USB, does not appear to be OP's problem, which is unresponsive DVD drive.

@OP

It is permissible to "bump" your thread every 12 hours. Not all helpers see or respond to queries with alacrity, nor should you expect them to. I have also moved your question to "Hardware" as the more appropriate subforum.

---

### Post by Yellow Pasque on 2017-12-23
I would start here:
```
sudo lshw -C disk
cd-drive
```

---

### Post by a-web on 2017-12-26
```
:~$ sudo lshw -C disk
  *-disk                    
       description: SCSI Disk
       product: DataTraveler 2.0
       vendor: Kingston
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       version: 0000
       serial: 12345678123456781234567812345678
       size: 7398MiB (7757MB)
       capabilities: removable
       configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdb
          size: 7398MiB (7757MB)
          capabilities: partitioned partitioned:dos
          configuration: signature=130d2169
  *-disk
       description: ATA Disk
       product: WDC WD1600BEVT-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1A01
       serial: WD-WXF1A10D5608
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=598f8ff8
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GT10N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
```

---

### Post by Yellow Pasque on 2017-12-26
It looks good, unless you had a disc inserted when you ran the command because it says "status=nodisc"

Put it in an audio CD and try playing it:
```
cdda-player -p -v /dev/sr0
```

---

### Post by a-web on 2017-12-27
with audio disk in:
```
sudo lshw -C disk
  *-disk                    
       description: ATA Disk
       product: WDC WD1600BEVT-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1A01
       serial: WD-WXF1A10D5608
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=598f8ff8
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GT10N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

and
```
cdda-player -p -v /dev/sr0
open /dev/sr0... ok
action: read toc...
++ WARN: error in ioctl CDROMREADTOCHDR: No medium found

++ WARN: error in ioctl CDROMREADTOCHDR: No medium found

++ WARN: error in ioctl CDROMREADTOCHDR: No medium found

error: read toc header: No medium found
action: 
   INFO: ioctl CDROMSUBCHNL failed: No medium found

error: read subchannel: No medium found
   INFO: ioctl CDROMSUBCHNL failed: No medium found

error: read subchannel: No medium found
action: read toc...
++ WARN: error in ioctl CDROMREADTOCHDR: No medium found

++ WARN: error in ioctl CDROMREADTOCHDR: No medium found

++ WARN: error in ioctl CDROMREADTOCHDR: No medium found

error: read toc header: No medium found
action: 
   INFO: ioctl CDROMSUBCHNL failed: No medium found

error: read subchannel: No medium found


```

---

### Post by Yellow Pasque on 2017-12-27
Still not recognizing that a disc is in the drive..

1. Try different discs
2. Boot a LiveUSB to make sure it's not a problem with your installation of Ubuntu
3. Check to see if there are firmware updates available for the drive. I found this, but I have no clue if it would work on non-Dells: [http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=R297895](http://www.dell.com/support/home/us/en/04/Drivers/DriversDetails?driverId=R297895)

EDIT: Oh, and before someone else suggests it, the lens could be dirty.

---

### Post by a-web on 2017-12-27
Thanks!

1. Different discs have the same outcome (or lack thereof).
2. Doesn't work with LiveUSB.
3. I'm not sure how I check for firmware updates...  I'll search around and report back.
REPORTING BACK: I looked around for how to do a firmware update.  And I don't understand what I found.  My drive is "HL-DT-STDVDRAM GT10N".  Any further insight or help?

Added: The lens has been cleaned.

---

