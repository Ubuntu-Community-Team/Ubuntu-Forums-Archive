---
title: "USB woes... Please help."
date: 2010-10-02
forum: Hardware
---

### Post by qwertyface on 2010-10-02
Hi all,

My USB stick has suddenly stopped working on me. I haven't a clue why but hopefully one of you smart lot might!

When I plug it in I can navigate to "Computer" and see the icon for the Lexar Jump Drive, but when I right click > properties, all the statistics that would usually be there such as size, etc, and file system all state "unknown".

For more technical information, when I plug it in doing the [COLOR=Lime]lsusb[/COLOR] command gives:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 003: ID 192f:0416 Avago Technologies, Pte. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ca:1812 Ricoh Co., Ltd Pavilion Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=Orange]Bus 001 Device 009: ID 05dc:a795 Lexar Media, Inc. [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```And as you can see it is detected. However, the good news stops there!

It does not get mounted to a [COLOR=Lime]/dev/sd*[/COLOR] device.

From the [COLOR=Lime]cat /var/log/messages | tail -20[/COLOR] command gives:

```

[ 1100.992734] usb 3-2: pl2303 converter now attached to ttyUSB0
[ 1332.750741] usb 1-1: USB disconnect, address 6
[ 1350.040051] usb 1-1: new high speed USB device using ehci_hcd and address 8
[ 1350.175817] usb 1-1: configuration #1 chosen from 1 choice
[ 1350.176908] scsi9 : SCSI emulation for USB Mass Storage devices
[ 1357.093887] scsi 9:0:0:0: Direct-Access     Lexar    USB Flash Drive  1100 PQ: 0 ANSI: 0 CCS
[ 1357.095220] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 1357.099410] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 1410.084093] usb 1-1: USB disconnect, address 8
[ 1437.248049] usb 1-1: new high speed USB device using ehci_hcd and address 9
[ 1437.384151] usb 1-1: configuration #1 chosen from 1 choice
[ 1437.384854] scsi10 : SCSI emulation for USB Mass Storage devices
[ 1444.296842] scsi 10:0:0:0: Direct-Access     Lexar    USB Flash Drive  1100 PQ: 0 ANSI: 0 CCS
[ 1444.298744] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 1444.307009] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 2388.965028] CE: hpet increasing min_delta_ns to 15000 nsec
[ 2412.894915] usb 1-1: USB disconnect, address 9
[ 2418.364056] usb 1-1: new high speed USB device using ehci_hcd and address 10
[ 2418.500447] usb 1-1: configuration #1 chosen from 1 choice
[ 2418.501156] scsi11 : SCSI emulation for USB Mass Storage devices

```I am baffled by the SCSI as I do not have any SCSI devices connected to my machine.

Here is my output from[COLOR=Lime] ls -l /dev/disk/by-id [/COLOR]when I have the USB stick attached:

```

total 0
lrwxrwxrwx 1 root root  9 2010-10-02 16:30 ata-FUJITSU_MHW2160BH_PL_K10NT772G5SE -> ../../sda
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 ata-FUJITSU_MHW2160BH_PL_K10NT772G5SE-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 ata-FUJITSU_MHW2160BH_PL_K10NT772G5SE-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 ata-FUJITSU_MHW2160BH_PL_K10NT772G5SE-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 ata-FUJITSU_MHW2160BH_PL_K10NT772G5SE-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 ata-FUJITSU_MHW2160BH_PL_K10NT772G5SE-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 ata-FUJITSU_MHW2160BH_PL_K10NT772G5SE-part8 -> ../../sda8
lrwxrwxrwx 1 root root  9 2010-10-02 16:30 scsi-SATA_FUJITSU_MHW2160K10NT772G5SE -> ../../sda
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 scsi-SATA_FUJITSU_MHW2160K10NT772G5SE-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 scsi-SATA_FUJITSU_MHW2160K10NT772G5SE-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 scsi-SATA_FUJITSU_MHW2160K10NT772G5SE-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 scsi-SATA_FUJITSU_MHW2160K10NT772G5SE-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 scsi-SATA_FUJITSU_MHW2160K10NT772G5SE-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 scsi-SATA_FUJITSU_MHW2160K10NT772G5SE-part8 -> ../../sda8
[COLOR=Orange]lrwxrwxrwx 1 root root  9 2010-10-02 16:52 usb-Lexar_USB_Flash_Drive_SGB9WBOP1GFE96I3E23D-0:0 -> ../../sdb[/COLOR]
lrwxrwxrwx 1 root root  9 2010-10-02 16:30 wwn-0x500000e04083253d -> ../../sda
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 wwn-0x500000e04083253d-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 wwn-0x500000e04083253d-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 wwn-0x500000e04083253d-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 wwn-0x500000e04083253d-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 wwn-0x500000e04083253d-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2010-10-02 16:30 wwn-0x500000e04083253d-part8 -> ../../sda8

```As you can see it is detected. The problem seems to be skirted around the device not being assigned correctly to a /dev/sd*.

Any ideas how I can solve this? The memory stick holds my dissertation on it! (I do of course have a back up version but I made that back up one week ago and I have added considerable amounts to it since then and I don't want to be put back a week - I can foresee this situation being a valuable lesson learned...).

Thanks
QF.

---

### Post by lidex on 2010-10-02
No expert here, but you could eliminate the usb stick as the culprit by plugging it into another computer or booting into a LiveCD or windows install - if available.

---

### Post by qwertyface on 2010-10-03
> **lidex said:**
> No expert here, but you could eliminate the usb stick as the culprit by plugging it into another computer or booting into a LiveCD or windows install - if available.

Hi. I tried that and then moved into linux to try to see what the root of the problem was because linux grants more access to the hardware.

I've been doing some more looking around and physically, on the inside, there are three IC's. Two are the memory chip and the other the controller IC. It is my belief that the NAND IC's are dead with the memory controller still active hence why the USB partially plays game with my laptop - this would also explain why the flash drive is only recognized and never mounted.

Perhaps I left it on the microwave or near a magnet...

---

### Post by moonbug on 2011-01-14
had a usb that died on a mates computer . tried it on mine works ok . plugged it back in his and nothing ,  i copied stuff to a second drive and got the data on his machine ok .. 
so try that . hope that helps

---

