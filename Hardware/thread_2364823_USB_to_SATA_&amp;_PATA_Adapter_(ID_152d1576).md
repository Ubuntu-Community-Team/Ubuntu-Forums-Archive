---
title: "USB to SATA &amp; PATA Adapter (ID 152d:1576)"
date: 2017-06-28
forum: Hardware
---

### Post by schnuckenack2 on 2017-06-28
Hello

after doing the following as recommended here [https://ubuntuforums.org/showthread.php?t=966321&page=2]("https://ubuntuforums.org/showthread.php?t=966321&page=2&")

> sudo modprobe pata_jmicron

the drive is still not working.

dmesg has the following output

> [  806.345217] usb 4-1: new SuperSpeed USB device number 3 using xhci_hcd
[  806.368213] usb 4-1: New USB device found, idVendor=152d, idProduct=1576
[  806.368219] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  806.368222] usb 4-1: Product: External Disk 3.0
[  806.368224] usb 4-1: Manufacturer: Jmicron
[  806.368226] usb 4-1: SerialNumber: 987654321010
[B][  806.370126] usb 4-1: USB controller 0000:03:00.0 does not support streams, which are required by the UAS driver.
[  806.370132] usb 4-1: Please try an other USB controller if you wish to use UAS.[/B]
[  806.370136] usb-storage 4-1:1.0: USB Mass Storage device detected
[  806.370339] scsi host5: usb-storage 4-1:1.0
[  807.369977] scsi 5:0:0:0: Direct-Access     USB                       0204 PQ: 0 ANSI: 6
[  807.370554] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  807.875930] sd 5:0:0:0: [sdb] 468862128 512-byte logical blocks: (240 GB/224 GiB)
[  807.876250] sd 5:0:0:0: [sdb] Write Protect is off
[  807.876255] sd 5:0:0:0: [sdb] Mode Sense: 47 00 00 08
[  807.876729] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  807.879987] sd 5:0:0:0: [sdb] Attached SCSI disk

What do the two bold lines mean? Anything I can do?

Thanks !

---

### Post by Yellow Pasque on 2017-06-28
It means "usb-storage" driver is used instead of UAS. [https://en.wikipedia.org/wiki/USB_Attached_SCSI](https://en.wikipedia.org/wiki/USB_Attached_SCSI)
I wouldn't worry about that message. I don't see anything in the snippet you shared that would indicate a problem. It looks like the disk is initialized as /dev/sdb. Does fdisk show partitions?
```
sudo fdisk -l
```

What kind of disk are you trying to use? What version of Ubuntu?

---

### Post by schnuckenack2 on 2017-06-29
> **Temüjin said:**
> It means "usb-storage" driver is used instead of UAS. [https://en.wikipedia.org/wiki/USB_Attached_SCSI](https://en.wikipedia.org/wiki/USB_Attached_SCSI)
I wouldn't worry about that message. I don't see anything in the snippet you shared that would indicate a problem. It looks like the disk is initialized as /dev/sdb. Does fdisk show partitions?
```
sudo fdisk -l
```

What kind of disk are you trying to use? What version of Ubuntu?

Hello Temüjin !

> fdisk -f

outputs the following

> 
Medium /dev/sda: 465,8 GiB, 500107862016 Bytes, 976773168 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 512 Bytes
I/O Größe (minimal/optimal): 512 Bytes / 512 Bytes
Typ der Medienbezeichnung: dos
Medienkennung: 0xdf84df84

Gerät      Boot     Start      Ende  Sektoren Größe Id Typ
/dev/sda1  *           63 529763825 529763763 252,6G  7 HPFS/NTFS/exFAT
/dev/sda2       529764350 976771071 447006722 213,2G  5 Erweiterte
/dev/sda5       968554496 976771071   8216576   3,9G 82 Linux Swap / Solaris
/dev/sda6       529764352 906246773 376482422 179,5G 83 Linux
/dev/sda7       906248192 968552447  62304256  29,7G 83 Linux

Die Einträge der Partitionstabelle stimmen nicht mit der Reihenfolge der Medien überein.


Medium /dev/sdb: 223,6 GiB, 240057409536 Bytes, 468862128 Sektoren

You're correct, /dev/sdb: 223,6GiB should be the SSD !

Ubuntu version is 16.04

Sincerely yours

---

### Post by schnuckenack2 on 2017-06-30
What can I do?

---

### Post by Michael_McKenney on 2017-06-30
Did you put it in an USB enclosure or just connect the USB converter to the drive and USB connection?   I would consider a better motherboard with more SATA connections instead of a converter.  Converters require drivers and usually don't have great performance and don't allow all features.

---

### Post by schnuckenack2 on 2017-07-01
It was meant to be used as an external drive.

---

### Post by schnuckenack2 on 2017-07-02
Is there, to begin with, any solution to that problem:

> [B][  806.370126] usb 4-1: USB controller 0000:03:00.0 does not support streams, which are required by the UAS driver.

[/B]And: 1) what are *streams*, 2) how do I query the available *usb controllers* and 3) how do I query whether or not they *support* streams[I] ?

Thanks
[/I]

---

### Post by schnuckenack2 on 2017-07-03
> **schnuckenack2 said:**
> Is there, to begin with, any solution to that problem:



[/B]And: 1) what are *streams*, 2) how do I query the available *usb controllers* and 3) how do I query whether or not they *support* streams[I] ?

Thanks
[/I]

I mean, isn't there a way to find out, whether the problem is incompatible hardware ?

---

