---
title: "mount antique dos drive"
date: 2010-01-21
forum: Hardware
---

### Post by argail1980 on 2010-01-21
Hi there,

I'm trying to rescue the data off an antique 240MB dos drive (Conner Peripherals 240MB ). I plugged it into an IDE->USB converter and tried to mount it. 
Judging from /var/log/messages (see below), the size is not recognized properly.

```
Jan 21 13:47:44 misspiggy kernel: [161280.505348] usb 8-1: new high speed USB device using ehci_hcd and address 3
Jan 21 13:47:45 mymachine kernel: [161280.638988] usb 8-1: configuration #1 chosen from 1 choice
Jan 21 13:47:45 mymachine kernel: [161280.643386] scsi9 : SCSI emulation for USB Mass Storage devices
Jan 21 13:47:50 mymachine kernel: [161285.633572] scsi 9:0:0:0: Direct-Access     Conner P eripherals 240MB      PQ: 0 ANSI: 2 CCS
Jan 21 13:47:50 mymachine kernel: [161285.635048] sd 9:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Jan 21 13:47:50 mymachine kernel: [161285.638537] sd 9:0:0:0: [sdb] READ CAPACITY(16) failed
Jan 21 13:47:50 mymachine kernel: [161285.638542] sd 9:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jan 21 13:47:50 mymachine kernel: [161285.638548] sd 9:0:0:0: [sdb] Use 0xffffffff as device size
Jan 21 13:47:50 mymachine kernel: [161285.638551] sd 9:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
Jan 21 13:47:50 mymachine kernel: [161285.639292] sd 9:0:0:0: [sdb] Write Protect is off
Jan 21 13:47:50 mymachine kernel: [161285.640534] sd 9:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Jan 21 13:47:50 mymachine kernel: [161285.644026] sd 9:0:0:0: [sdb] READ CAPACITY(16) failed
Jan 21 13:47:50 mymachine kernel: [161285.644030] sd 9:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jan 21 13:47:50 mymachine kernel: [161285.644036] sd 9:0:0:0: [sdb] Use 0xffffffff as device size
Jan 21 13:47:50 mymachine kernel: [161285.644039] sd 9:0:0:0: [sdb] 4294967296 512-byte hardware sectors (2199023 MB)
Jan 21 13:47:50 mymachine kernel: [161285.644781] sd 9:0:0:0: [sdb] Write Protect is off
Jan 21 13:47:50 mymachine kernel: [161285.644793]  sdb: unknown partition table
Jan 21 13:47:50 mymachine kernel: [161285.800582] sd 9:0:0:0: [sdb] Attached SCSI disk
Jan 21 13:47:50 mymachine kernel: [161285.800618] sd 9:0:0:0: Attached scsi generic sg2 type 0
Jan 21 13:58:27 mymachine -- MARK --
Jan 21 14:00:45 mymachine kernel: [162060.265592] usb 8-1: USB disconnect, address 3

```

mount says "wrong fs type..." etc.

and finally here comes the output of fdisk:

```
Platte /dev/sdb: 2199.0 GByte, 2199023255552 Byte
255 Köpfe, 63 Sektoren/Spuren, 267349 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xe45b4827

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System


```

sorry, all in German, but recognizable I hope.

Is there any method to tell ubuntu that it is an old disk and not to confuse MB with GB? (maybe this is not the real error at all...)

I appreciate any ideas.

Thanks..
argail

---

### Post by argail1980 on 2010-01-27
bump....

---

### Post by oldfred on 2010-01-27
How is your BIOS identifying it. Usually operating systems take their information from the BIOS settings?

I am more suspicious of the USB converter not converting it correctly. Do  you have and IDE/PATA port on your motherboard?

---

### Post by cascade9 on 2010-01-28
> **oldfred said:**
> How is your BIOS identifying it. Usually operating systems take their information from the BIOS settings?

I am more suspicious of the USB converter not converting it correctly. Do  you have and IDE/PATA port on your motherboard?

+1. A drive that old, modern do-dads like USB-> ATA converters might have issues when the BIOS would detect it fine.

---

