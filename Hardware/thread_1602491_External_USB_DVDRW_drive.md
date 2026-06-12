---
title: "External USB DVDRW drive"
date: 2010-10-21
forum: Hardware
---

### Post by CMos_UK on 2010-10-21
Hi there,

My father has an Acer Aspire One running Ubuntu Netbook 10.10.

He has just purchased an external DVD-RW drive and is trying to get it to work.  There are a couple of problems which seem to exist on my desktop as well (Ubuntu 10.10).

Firstly, the drive will not appear in the "Computer" section in Nautilus but I can play a DVD or CD from it by addressing it as "/dev/cdrom" or "/dev/dvd" in VLC.  When the drive is connected to a USB port you get the following in "/var/log/messages":

```
Oct 21 16:55:52 anticyclone kernel: [25044.368047] usb 1-2: new high speed USB device using ehci_hcd and address 6
Oct 21 16:55:52 anticyclone kernel: [25044.502883] usb-storage 1-2:1.0: Quirks match for vid 05e3 pid 0701: 520
Oct 21 16:55:52 anticyclone kernel: [25044.502937] scsi8 : usb-storage 1-2:1.0
Oct 21 16:55:53 anticyclone kernel: [25045.507282] scsi 8:0:0:0: CD-ROM            HL-DT-ST DVD-RW GWA-4040N 1.01 PQ: 0 ANSI: 0
Oct 21 16:55:54 anticyclone kernel: [25045.759855] sr1: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Oct 21 16:55:54 anticyclone kernel: [25045.760274] sr 8:0:0:0: Attached scsi generic sg4 type 5
```When you remove you get this:
```
Oct 21 16:56:23 anticyclone kernel: [25074.837417] usb 1-2: USB disconnect, address 6
```This all seems very normal ;-)


Secondly, I don't seem to be able to mount this drive.  I get the following error:
```
mount: can't find /dev/dvdrw1 in /etc/fstab or /etc/mtab
```If it helps here is the relevant output line from lsusb:
```
Bus 001 Device 006: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```Ideally, I would like the external DVD-RW drive to behave much like any internal drive on a desktop machine; it appears in "Computer" and when you insert media it is able to mount it (auto or otherwise).  Any help would be greatly appreciated.

Many thanks,

Charlie

---

### Post by abrahamthegrey on 2010-10-25
I'm going to bump this.  I have the same problem.  I run an Asus Eee PC 1005ha and am running Maverick.  The drive I'm using is a Sony DRX810-UL.  I am a beginner though, so I'm not exactly sure what else I can provide so that someone can help me.

Thanks in advance,

ABE

---

### Post by smattos on 2010-11-27
I'm having the same problem with my external CDROM drive connected to my Acer Aspire One.  The Disk Utility of Ubuntu 10.10 "sees" the drive, but nothing else does.  I have connected the drive to an alternate PC and it is immediately recognized by Windows 7.

Any help would be greatly appreciated.

---

### Post by coffeecat on 2010-11-27
Please have a look at this from the OP:

> **CMos_UK said:**
> here is the relevant output line from lsusb:
```
Bus 001 Device 006: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```

If lsusb with your dvd drive returns the device ID 05e3:0701, then you have the same issue as the OP, which is discussed more comprehensively in this thread:

[http://ubuntuforums.org/showthread.php?t=1618085](http://ubuntuforums.org/showthread.php?t=1618085)

There are some workarounds in that for Maverick depending on whether you are trying to read a data disc or media disc. Although there is a bug report for this (linked in that thread) there has been no movement by the devs and I very much doubt whether it will ever be fixed for Maverick seeing as this is an issue with very specific hardware.

If lsusb returns a different device ID, then I suggest you start your own new thread.

---

