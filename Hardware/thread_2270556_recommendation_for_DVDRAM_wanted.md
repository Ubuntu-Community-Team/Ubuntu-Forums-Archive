---
title: "recommendation for DVDRAM wanted"
date: 2015-03-24
forum: Hardware
---

### Post by bardo2 on 2015-03-24
Hi,

my Desktop is fairly new (XEON with ECC memory). I am happy with it, except for the CD drive. I can't write at all nor read from music CD's.
It is a DVDRAM GH24NSC0 which works without drivers in Windows (which i dont use). It is a fast combo burner (multi-format, (+/-) even blueray), but i suspect Linux may be lacking the appropriate API or driver.
I don't need Blueray, but a CD/DVD reader/writer that is working nicely with Ubuntu. My vendor is prepared to replace the drive, but he wants me to name a model. Can you help or point me to some help?

---

### Post by Yellow Pasque on 2015-03-24
Can you show:
```
sudo lshw -sanitize -C disk
```

---

### Post by bardo2 on 2015-03-24
> **Temüjin said:**
> Can you show:
```
sudo lshw -sanitize -C disk
```

```
  *-disk                  
       Beschreibung: ATA Disk
       Produkt: ST2000DM001-1ER1
       Hersteller: Seagate
       Physische ID: 0.0.0
       Bus-Informationen: scsi@0:0.0.0
       Logischer Name: /dev/sda
       Version: CC25
       Seriennummer: [REMOVED]
       Größe: 1863GiB (2TB)
       Fähigkeiten: gpt-1.00 partitioned partitioned:gpt
       Konfiguration: ansiversion=5 guid=8e25c410-b14e-4ba2-98fc-9b1d51dbb225 sectorsize=4096
  *-disk
       Beschreibung: ATA Disk
       Produkt: ST2000DM001-1ER1
       Hersteller: Seagate
       Physische ID: 0.0.0
       Bus-Informationen: scsi@1:0.0.0
       Logischer Name: /dev/sdb
       Version: CC25
       Seriennummer: [REMOVED]
       Größe: 1863GiB (2TB)
       Fähigkeiten: gpt-1.00 partitioned partitioned:gpt
       Konfiguration: ansiversion=5 guid=18014e4d-f2d9-463f-a5b5-6efa5939d947 sectorsize=4096
  *-disk
       Beschreibung: ATA Disk
       Produkt: ST2000DM001-1ER1
       Hersteller: Seagate
       Physische ID: 0.0.0
       Bus-Informationen: scsi@2:0.0.0
       Logischer Name: /dev/sdc
       Version: CC25
       Seriennummer: [REMOVED]
       Größe: 1863GiB (2TB)
       Fähigkeiten: gpt-1.00 partitioned partitioned:gpt
       Konfiguration: ansiversion=5 guid=d1018090-da71-4620-b350-4f7165a9d157 sectorsize=4096
  *-disk
       Beschreibung: ATA Disk
       Produkt: ST2000DM001-1ER1
       Hersteller: Seagate
       Physische ID: 0.0.0
       Bus-Informationen: scsi@3:0.0.0
       Logischer Name: /dev/sdd
       Version: CC25
       Seriennummer: [REMOVED]
       Größe: 1863GiB (2TB)
       Fähigkeiten: gpt-1.00 partitioned partitioned:gpt
       Konfiguration: ansiversion=5 guid=fef58687-a55f-4873-ae09-0f89638d48b4 sectorsize=4096
  *-disk
       Beschreibung: ATA Disk
       Produkt: Crucial_CT512MX1
       Physische ID: 0.0.0
       Bus-Informationen: scsi@4:0.0.0
       Logischer Name: /dev/sde
       Version: MU01
       Seriennummer: [REMOVED]
       Größe: 476GiB (512GB)
       Fähigkeiten: gpt-1.00 partitioned partitioned:gpt
       Konfiguration: ansiversion=5 guid=e255bc5a-9f0f-4c55-81c0-c1b64abb2f58 sectorsize=4096
  *-disk
       Beschreibung: ATA Disk
       Produkt: Solidata   SSD
       Physische ID: 0.0.0
       Bus-Informationen: scsi@5:0.0.0
       Logischer Name: /dev/sdf
       Version: 0.1
       Seriennummer: [REMOVED]
       Größe: 59GiB (64GB)
       Fähigkeiten: gpt-1.00 partitioned partitioned:gpt
       Konfiguration: ansiversion=5 guid=cafd8f1f-fad1-4216-8f4d-ae379c069123 sectorsize=512
  *-disk
       Beschreibung: ATA Disk
       Produkt: ST2000DM001-1ER1
       Hersteller: Seagate
       Physische ID: 0.0.0
       Bus-Informationen: scsi@6:0.0.0
       Logischer Name: /dev/sdg
       Version: CC25
       Seriennummer: [REMOVED]
       Größe: 1863GiB (2TB)
       Fähigkeiten: gpt-1.00 partitioned partitioned:gpt
       Konfiguration: ansiversion=5 guid=9d16a72e-1a8a-4312-bba9-b74d2721e761 sectorsize=4096
  *-disk
       Beschreibung: ATA Disk
       Produkt: ST2000DM001-1ER1
       Hersteller: Seagate
       Physische ID: 0.0.0
       Bus-Informationen: scsi@7:0.0.0
       Logischer Name: /dev/sdh
       Version: CC25
       Seriennummer: [REMOVED]
       Größe: 1863GiB (2TB)
       Fähigkeiten: gpt-1.00 partitioned partitioned:gpt
       Konfiguration: ansiversion=5 guid=03cc41b0-145d-49af-a425-a33b491900e9 sectorsize=4096
  *-cdrom
       Beschreibung: DVD-RAM writer
       Produkt: DVDRAM GH24NSC0
       Hersteller: HL-DT-ST
       Physische ID: 0.0.0
       Bus-Informationen: scsi@10:0.0.0
       Logischer Name: /dev/cdrom
       Logischer Name: /dev/sr0
       Version: LK00
       Fähigkeiten: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       Konfiguration: ansiversion=5 status=nodisc

```
Woah, are you intending to examine, if there is a driver somewhere? Or none necessary?

---

### Post by Yellow Pasque on 2015-03-24
I'm not too advanced with troubleshooting CD drives (my drive always worked fine "out of the box"), but perhaps if you give enough information, someone will see an issue that can be corrected. If you are able, give output of cd-drive command, which is more thorough than lshw):

```
sudo apt-get install libcdio-utils  #it may already be installed
cd-drive
```

---

### Post by bardo2 on 2015-03-24
hey, cool, never encountered that one...
```
cd-drive version 0.83 x86_64-pc-linux-gnu
Copyright (c) 2003, 2004, 2005, 2007, 2008, 2011 R. Bernstein
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
The driver selected is GNU/Linux
The default device for this driver is /dev/cdrom

Drivers available...
  GNU/Linux ioctl and MMC driver     
  cdrdao (TOC) disk image driver     
  bin/cuesheet disk image driver     
  Nero NRG disk image driver         

CD-ROM drive supports MMC 3

                       Drive: /dev/cdrom
Vendor                      : HL-DT-ST
Model                       : DVDRAM GH24NSC0 
Revision                    : LK00
Profile List Feature
    DVD-R - Double-Layer Sequential Recording
    DVD-R - Double-layer Jump Recording
    DVD+R Double Layer - DVD Recordable Double Layer
    DVD+R - DVD Recordable
    DVD+RW - DVD Rewritable
    Re-recordable DVD using Sequential Recording
    Re-recordable DVD using Restricted Overwrite
    Re-writable DVD
    Re-recordable DVD using Sequential recording
    Read only DVD
    CD-RW Re-writable Compact Disc capable
    Write once Compact Disc capable
    Read only Compact Disc capable

Core Feature

Morphing Feature
    Operational Change Request/Notification supported
    Synchronous GET EVENT/STATUS NOTIFICATION supported

Removable Medium Feature
    Tray type loading mechanism
    can eject the medium or magazine via the normal START/STOP command
    can be locked into the Logical Unit

Write Protect Feature

Random Readable Feature

Multi-Read Feature

CD Read Feature
    C2 Error pointers are supported
    CD-Text is supported

DVD Read Feature

Random Writable Feature

Incremental Streaming Writable Feature

Formattable Feature

Management Ability of the Logical Unit/media system to provide an apparently defect-free space. Feature

Restricted Overwrite Feature

DVD+RW Feature

DVD+R Feature

Rigid Restricted Overwrite Feature

CD Track at Once Feature

CD Mastering (Session at Once) Feature

DVD-R/RW Write Feature

Unknown code 33 Feature

Profile List Feature

Profile List Feature

Unknown code 95 Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Profile List Feature

Hardware                                  : CD-ROM or DVD
Can eject                                 : Yes
Can close tray                            : Yes
Can disable manual eject                  : Yes
Can select juke-box disc                  : No

Can set drive speed                       : No
Can read multiple sessions (e.g. PhotoCD) : Yes
Can hard reset device                     : Yes

Reading....
  Can read Mode 2 Form 1                  : Yes
  Can read Mode 2 Form 2                  : Yes
  Can read (S)VCD (i.e. Mode 2 Form 1/2)  : Yes
  Can read C2 Errors                      : Yes
  Can read IRSC                           : Yes
  Can read Media Channel Number (or UPC)  : Yes
  Can play audio                          : Yes
  Can read CD-DA                          : Yes
  Can read CD-R                           : Yes
  Can read CD-RW                          : Yes
  Can read DVD-ROM                        : Yes

Writing....
  Can write CD-RW                         : Yes
  Can write DVD-R                         : Yes
  Can write DVD-RAM                       : Yes
  Can write DVD-RW                        : No
  Can write DVD+RW                        : No

```

---

### Post by Yellow Pasque on 2015-03-24
All of the diagnostic information looks as expected to me. What programs are you using to try and play audio cd's and burn discs?

If you put an audio CD in the drive and try and play it using the following command, what happens?
```
cdda-player -v -p /dev/cdrom
```

---

### Post by bardo2 on 2015-03-24
After inserting an Audio-CD (from a store, not a copy!), Rhythmbox wants to take over, but doesnt even display the number of tracks.

The commandline gives:
```
open /dev/cdrom... ok
action: read toc...
action: 
action: play track 1 to track 13.
action: play track 1 to track 13.
```

followed by - extended silence. drive doesnt seem to be moving. eject is possible.

btw: mp3-files are playing just fine with rhythmbox.

---

### Post by Yellow Pasque on 2015-03-24
After reading more about cdda-player, it's probably not a good program to test with. Quite honestly, I can't remember the last time I actually played an audio CD in my computer (the only thing I do with audio CD's is rip them to FLAC).
I'm sure there are other people who can help you better here. If your drive worked in Windows, there's no reason it shouldn't work in Linux though. It's probably something stupid like your user isn't in the cdrom group.

---

### Post by bardo2 on 2015-03-24
Ok, let me restate the initial problem: i dont need my DVDRAM to work, i would like to know ahead if time a drive model that works. I have been hinted towards Samsung (they are cheap), but there are many models available. Can anyone confirm a specific one to offer support for CD/DVD +/- read/write audio/data (and meaningful combinations thereof)?

---

### Post by Yellow Pasque on 2015-03-24
> i dont need my DVDRAM to work
Throwing money at a problem does not always fix it. If something is physically wrong with your drive, then replace it. If the drive itself is not damaged, then something is probably wrong with your configuration and a replacement drive could easily have the same issue(s). CD drives don't use highly specialized kernel modules/drivers (like a video card would). Think of it like a simple USB mouse - if you have issues with the cursor and your mouse works fine in other OS's or systems, then solving the issue with a different mouse seems unlikely.

Nevertheless, it's your money, so I personally can vouch for a Samsung SH-203B (with firmware revision SB04). I've had it for 4 or 5 years now, so I'm not sure if it's still available for sale.
Good luck.

EDIT: i never burned a DVD-RAM, so I don't know if that works as advertised.

---

### Post by bardo2 on 2015-03-25
Excellent! Someone got my request right. :-)
Immediately looked it up, the drive you are suggesting is 8 years old and can - by now - only be bought in india (pretty close though) ;-)
Well, i promise, on my last pc, i used the cd-drive maybe 2 times a month, still, i want it. The brand new drive i have just doesnt work. and since it has blueray support (among others), i guess this is just too much for the "mouse" to handle. ;-)

Weird part with the current one: i can read data from it. But nothing else (no write, no audio) and i am sceptical about a possible misconfig. The OS is only few weeks from standard install away and i did not mess with anything CD related. Also, i *could* reset the install to initial values (have a backup ready), just no fun then. Plenty of missing scripts/tools would be the onus.

Finally: no money involved. my vendor promised to replace the drive from the very beginning, when i still had much more serious issues with the setup, wasnt even sure if Ubuntu could run. (And still i am waiting for newer kernel releases for mcelog to work properly). So all has been payed by now.

---

