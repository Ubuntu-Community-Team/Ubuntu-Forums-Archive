---
title: "Speeding up CD-ROM"
date: 2005-09-14
forum: Hardware &amp; Laptops
---

### Post by robfindlay on 2005-09-14
Okay i'm trying to execute the following: [http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)

I get the following error mesage: 
/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

This is on a dell 6000 laptop, I'm including the lspci: 

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:03:01.2 0805: Ricoh Co Ltd: Unknown device 0822 (rev 17)
0000:03:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)


I'm officially at a loss, can someone help?

---

### Post by mlomker on 2005-09-14
Are you sure that your cdrom is called /dev/cdrom?  Mine isn't.

Post the output of this command:

```

sudo dmesg | grep CD

```

---

### Post by robfindlay on 2005-09-15
[QUOTE=mlomker]Are you sure that your cdrom is called /dev/cdrom?  Mine isn't.

Post the output of this command:

```

sudo dmesg | grep CD

```[/QUOTE]


Here it is... 
------------------
 Vendor: PHILIPS   Model: CDRW/DVD SCB5265  Rev: TD15
  Type:   CD-ROM                             ANSI SCSI revision: 05
Uniform CD-ROM driver Revision: 3.20
Attached scsi CD-ROM sr0 at scsi1, channel 0, id 0, lun 0
-----------------

So tried this command: sudo hdparm -d1 /dev/sr0

And got this result: 
-----------------------------
/dev/sr0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
-----------------------------
How the freak did I wind up with a SCSI cdrom drive?  If I remember correctly 
I don't think SCSI uses DMA.  I could be wrong though. 


Rob Findlay

---

### Post by mlomker on 2005-09-16
> 
How the freak did I wind up with a SCSI cdrom drive?  If I remember correctly 
I don't think SCSI uses DMA.  I could be wrong though. 


It's probably a SATA CD-Rom drive.  Linux does not have native SATA support, so the drivers do some tricks to make it look like a SCSI drive to the operating system.  You're correct, the hdparm settings won't work.

What makes you believe it is slow?  Have you done some timed transfers or tried burning a CD at high speed?  Video not playing well?

---

### Post by Pancetilla on 2005-10-04
I've got the same problem, cannot watch DVDs properly in the laptopbecause of this. Has anyone tried blktool in Ubuntu for speeding up SATA CD-ROM????
[http://sourceforge.net/project/showfiles.php?group_id=3242&package_id=127086]("sourceforge  blktool")

---

