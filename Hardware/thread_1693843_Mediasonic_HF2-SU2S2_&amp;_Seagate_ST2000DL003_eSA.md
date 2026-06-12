---
title: "Mediasonic HF2-SU2S2 &amp; Seagate ST2000DL003 eSATA"
date: 2011-02-23
forum: Hardware
---

### Post by canclan on 2011-02-23
OK, so I have the following media server/torrent server setup:

Gigabyte GA-MA785GM-US2H
6GB ram
Seagate (ST31000528AS) running Turnkey Torrent appliance
WDC WD15EARS-00Z (internal storage)
2xSeagate Freeagent External USB drives (1 & 1.5 TB)


and I installed a StarTech PCI Express card with an eSATA card so that I could use the eSata connection speed with a Mediasonic HF2-SU2S2 external four bay enclosure.  I had two SAMSUNGs (Spinpoint F4 HD204UI) and just bought two Seagates (Barracuda Green  ST2000DL003).  The Mediasonic has both USB and eSata connectors.  When I install all the drives and use USB mode, all four drives mount fine.  When I use the eSata, only the Samsungs are seen no matter which slots I put them in - or whether the Samsungs are installed or not.  What seems wierd to me, is that the Seagates *seem* to be listed in the /dev folder, but the kernel can not mount the drives (see error below).  I tried formatting (ext3) the Seagates using Webmin, using webshell (Shell in a Box), and using another linux box (10.10), all without any success in mounting the Seagate drives.  I am really stumped on this one.  The Samsungs mount fine in both USB and eSata modes, but the Seagates will only mount in USB mode.  BTW, not set up as RAID - just 8TB storage.

Does anyone have any idea(s) about what is going on or have any suggestions as to what I could try?  If there is any more info/outputs I can provide, please ask!

Thanks in advance for any and all help!



Some outputs and hardware links:

```
ls /dev/by-path
pci-0000:00:11.0-scsi-0:0:0:0
pci-0000:00:11.0-scsi-0:0:0:0-part1
pci-0000:00:11.0-scsi-0:0:0:0-part2
pci-0000:00:11.0-scsi-0:0:0:0-part5
pci-0000:00:11.0-scsi-1:0:0:0
pci-0000:00:11.0-scsi-1:0:0:0-part1
pci-0000:00:12.2-usb-0:3:1.0-scsi-0:0:0:0
pci-0000:00:12.2-usb-0:3:1.0-scsi-0:0:0:0-part1
pci-0000:00:12.2-usb-0:4:1.0-scsi-0:0:0:0
pci-0000:00:12.2-usb-0:4:1.0-scsi-0:0:0:0-part1
pci-0000:00:14.1-scsi-0:0:0:0
pci-0000:02:00.0-scsi-0:0:0:0
pci-0000:02:00.0-scsi-2:0:0:0
``````
ls /dev/by-id
ata-ST2000DL003-9VT166_5YD22TY8
ata-ST2000DL003-9VT166_5YD238RM
ata-ST31000528AS_9VP5N8RG
ata-ST31000528AS_9VP5N8RG-part1
ata-ST31000528AS_9VP5N8RG-part2
ata-ST31000528AS_9VP5N8RG-part5
ata-WDC_WD15EARS-00Z5B1_WD-WMAVU2789320
ata-WDC_WD15EARS-00Z5B1_WD-WMAVU2789320-part1
by-id.txt
scsi-1ATA_ST2000DL003-9VT166_5YD22TY8
scsi-1ATA_ST2000DL003-9VT166_5YD238RM
scsi-1ATA_ST31000528AS_9VP5N8RG
scsi-1ATA_ST31000528AS_9VP5N8RG-part1
scsi-1ATA_ST31000528AS_9VP5N8RG-part2
scsi-1ATA_ST31000528AS_9VP5N8RG-part5
scsi-1ATA_WDC_WD15EARS-00Z5B1_WD-WMAVU2789320
scsi-1ATA_WDC_WD15EARS-00Z5B1_WD-WMAVU2789320-part1
usb-Seagate_FreeAgent_2GEVVT48-0:0
usb-Seagate_FreeAgent_2GEVVT48-0:0-part1
usb-Seagate_FreeAgent_2GEVXAJM-0:0
usb-Seagate_FreeAgent_2GEVXAJM-0:0-part1
```Mount Error
```
mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
``````
dmesg|tail
1227.389657] VFS: Can't find ext3 filesystem on dev sde1.

```the Seagates are sde & sdf.  The Samsungs are sdg & sdh.


Hardware/software:
Mediasonic HF2-SU2S2 Pro Box
[http://ain.mediasonic.ca/store/product_info.php?products_id=150](http://ain.mediasonic.ca/store/product_info.php?products_id=150)

Seagate Barracuda® Green SATA 6Gb/s 2TB Hard Drive ST2000DL003 
[http://www.seagate.com/ww/v/index.jsp?name=st2000dl003-bcuda-green-sata-6gb-2tb-hd&vgnextoid=add6439d45c0b210VgnVCM1000001a48090aRCRD&locale=en-US](http://www.seagate.com/ww/v/index.jsp?name=st2000dl003-bcuda-green-sata-6gb-2tb-hd&vgnextoid=add6439d45c0b210VgnVCM1000001a48090aRCRD&locale=en-US)

SAMSUNG Spinpoint F4 HD204UI 
[http://www.samsung.com/global/business/hdd/productmodel.do?type=94&subtype=98&model_cd=552](http://www.samsung.com/global/business/hdd/productmodel.do?type=94&subtype=98&model_cd=552)

StarTech PCI Express SATA Controller Card Adapter PEXSAT31E1
[http://us.startech.com/product/PEXSAT31E1-1x-eSATA-1x-SATA-6-Gbps-PCI-Express-SATA-Controller-Adapter-Card](http://us.startech.com/product/PEXSAT31E1-1x-eSATA-1x-SATA-6-Gbps-PCI-Express-SATA-Controller-Adapter-Card)

Turney Torrent Appliance (Hardy 8.04 core - version 2009.10-2 I think)
[http://www.turnkeylinux.org/torrentserver](http://www.turnkeylinux.org/torrentserver)

---

### Post by canclan on 2011-03-22
Never mind.  Turnkey upgraded to 10.04 and now it all works.

---

