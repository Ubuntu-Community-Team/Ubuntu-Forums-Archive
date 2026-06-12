---
title: "hp dv2550se problems"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by crex on 2007-07-22
I have a HP dv2550se.  I get the following error when trying to mount a cd/dvd. I´m running 7.04.
I could use a little help to get it working. This is my first time running ubuntu and I am glad most things work. I just want to get the dvd burner working.

Thanks 
Rey

unable to mount the selected volume
mount: special device /dev/hda does not exist


~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4353 (rev 14)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by EXCiD3 on 2007-07-23
Can you explain EXCATLY what you do when this occurs?

---

### Post by crex on 2007-07-24
When i insert a cd/dvd into the dvd reader it doesn´t  auto mount the disc. So I open Nautilus and click on CD-ROM 1. The error that I stated in my first post pops up. I tried to mount /dev/hda in a terminal but the same error is shown. What is weird is my fstab shows /dev/hda being mounted to /media/cdrom0. Below is my fstab just in case you need it.

Thanks for the reply 
Rey

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=3bd27bdd-f488-41a7-a582-245f00136e7e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b0d19519-b10a-4da0-8c8f-0a214083582e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by crex on 2007-07-25
Ok well to get the cdrom to work and mount, I needed to modprobe piix. It works now the only thing is now the audio doesn't work. I will keep working on  this but if anyone has any suggestions I'm all ears. 

Rey

---

### Post by buntunub on 2007-07-25
Does it work with Data CDs? If you are trying to run multimedia did you install the necessary codecs and set the zone?

---

### Post by crex on 2007-07-25
> **buntunub said:**
> Does it work with Data CDs? If you are trying to run multimedia did you install the necessary codecs and set the zone?

Yes i did install all codecs. The laptop stopped producing sound. When first starting up ubuntu it use to have audio but now no audio works. I have to go to work but I'll look around for a fix later. 

Thanks,
Rey

---

