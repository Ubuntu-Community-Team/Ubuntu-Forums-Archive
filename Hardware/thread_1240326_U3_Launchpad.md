---
title: "U3 Launchpad"
date: 2009-08-14
forum: Hardware
---

### Post by Nathan.Flow on 2009-08-14
Ok so I decided to start a thread, after all my searches for U3 in the Ubuntu forms. 
If you don't know what U3 is, U3 is a program that is hard coded to ScanDisk Cruzer Micro usb thumb drives. This program auto lunches and install it's self in windows. 
Why do we care if we use linux?
Simple, the U3 program runs of a hard coded "CD" emulated part of the thumb drive, this can be a huge security risk. Although the cd portion of the device doesn't load automatically in linux, the penitential problem for security and just plane nuisance still exists. What I mean by nuisance is, if you connect the drive to a windows system the embedded U3 program copies it's folders and programs back to the root of the thumb drive, if your using the device (thumb drive) for specific reasons this could cause problems with shortcuts, space requirements or what ever.

Why am I starting a new thread? Well I have a challenge for the lunix community at large. 

Either make a package to remove the read only "CD emulation" form the device.
Or 
Find some other way of whipping this thing completely so the embedded "CD" emulation no longer exists. 

What I've found so far.
The site for U3 does have a uninstaller, A very hard to find one, but after some google cash searching I finally found a copy of the program.
I don't believe the uninstaller completely removes the Embedded "cd" part of the drive thus still proposing a security risk.

Thank you.

---

### Post by Nathan.Flow on 2009-08-14
the site for the uninstaller
[http://u3.com/support/default.aspx#CQ3](http://u3.com/support/default.aspx#CQ3)

out put of dmeag | tail

```

[ 6410.425743] usb 1-1: new high speed USB device using ehci_hcd and address 25
[ 6410.484077] usb 1-1: configuration #1 chosen from 1 choice
[ 6410.484280] scsi28 : SCSI emulation for USB Mass Storage devices
[ 6410.484474] usb-storage: device found at 25
[ 6410.484477] usb-storage: waiting for device to settle before scanning
[ 6412.481438] usb-storage: device scan complete
[ 6412.482271] scsi 28:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[ 6412.483060] scsi 28:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0
[ 6412.485054] sd 28:0:0:0: [sdc] 3907583 512-byte hardware sectors (2001 MB)
[ 6412.486196] sd 28:0:0:0: [sdc] Write Protect is off
[ 6412.486199] sd 28:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 6412.486202] sd 28:0:0:0: [sdc] Assuming drive cache: write through
[ 6412.489448] sd 28:0:0:0: [sdc] 3907583 512-byte hardware sectors (2001 MB)
[ 6412.490604] sd 28:0:0:0: [sdc] Write Protect is off
[ 6412.490610] sd 28:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 6412.490612] sd 28:0:0:0: [sdc] Assuming drive cache: write through
[ 6412.490618]  sdc: sdc1
[ 6412.492227] sd 28:0:0:0: [sdc] Attached SCSI removable disk
[ 6412.492272] sd 28:0:0:0: Attached scsi generic sg3 type 0
[ 6412.503780] sr1: scsi3-mmc drive: 48x/48x tray
[ 6412.503841] sr 28:0:0:1: Attached scsi CD-ROM sr1
[ 6412.503883] sr 28:0:0:1: Attached scsi generic sg4 type 5


```

oh yea one more thing I've already tired using dd to write all zeros to the drive, as well as random data.

---

### Post by ajgreeny on 2009-08-14
I don't know if this is what you are wanting, but have you tried dban.  This is used to completely wipe drives and make all data non-recoverable, so I assume it would do what you are trying to do.  It does not work on individual partitions, but whole drives, so ought to get rid of everything on the usb drive, as far as I can see.
[http://www.dban.org/](http://www.dban.org/)

---

### Post by Nathan.Flow on 2009-08-15
> **ajgreeny said:**
> I don't know if this is what you are wanting, but have you tried dban.  This is used to completely wipe drives and make all data non-recoverable, so I assume it would do what you are trying to do.  It does not work on individual partitions, but whole drives, so ought to get rid of everything on the usb drive, as far as I can see.
[http://www.dban.org/](http://www.dban.org/)

Thanks for your input, as far as I understand dban uses the linux command ```
for n in `seq 7`; do sudo dd if=/dev/random of=/dev/DestinationDrive bs=8b conv=notrunc; done
```, How this is going to remove the "embeded" read only part that is detected as a cd rom I don't know and I'm unsure but I'll do some testing and post my results tomorrow.:popcorn:

---

