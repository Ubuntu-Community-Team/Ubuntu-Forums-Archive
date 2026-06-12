---
title: "[SOLVED] 16Gb USB-flash Drive from Corsair do not auto mountig"
date: 2008-10-13
forum: Hardware
---

### Post by Pha[N]toM on 2008-10-13
Hello, I have some problem. Today i've buy 16Gb USB-flash Drive from Corsair.

When I put it into my laptop he (USB-FLASH, may-be "she") blinks his blue diode and not automounts onto system (Ubuntu 8.04.1, x86-64)

dmesg, after putting flash-stick in to the usb-hole tells:
```
[15018.849872] usb 6-1: new high speed USB device using ehci_hcd and address 6
[15018.987834] usb 6-1: configuration #1 chosen from 1 choice
[15019.006898] scsi9 : SCSI emulation for USB Mass Storage devices
[15019.013826] usb-storage: device found at 6
[15019.013831] usb-storage: waiting for device to settle before scanning
[15024.005605] usb-storage: device scan complete
[15024.006841] scsi 9:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS
[15024.018061] sd 9:0:0:0: [sdb] 32112640 512-byte hardware sectors (16442 MB)
[15024.019066] sd 9:0:0:0: [sdb] Write Protect is off
[15024.019073] sd 9:0:0:0: [sdb] Mode Sense: 43 00 00 00
[15024.019075] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[15024.022287] sd 9:0:0:0: [sdb] 32112640 512-byte hardware sectors (16442 MB)
[15024.023286] sd 9:0:0:0: [sdb] Write Protect is off
[15024.023290] sd 9:0:0:0: [sdb] Mode Sense: 43 00 00 00
[15024.023292] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[15024.023298]  sdb: sdb1
[15024.075216] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[15024.075260] sd 9:0:0:0: Attached scsi generic sg2 type 0
```
when I
```
sudo mount -t vfat -o user /dev/sdb1 /media/fat
```

I've got a mounted flash-drive, but I can't write into it.

Waiting for Help! Thanx! And..... sorry for my eagly english

---

### Post by Pha[N]toM on 2008-10-13
So... this problem... it really [COLOR="Red"]**solved**[/COLOR].
I use gparted. For first I've format flash drive in ReiserFS, put it away and put it back in the (usb)hole. Flash drive has mounted in RW-mode, I test it, all is OK (and writing >2Gb files). 
Today morning, I've format it to the FAT32, remove and put back and it works fine!
(I try to write files, larger than 2Gb, and they are writes correctly...)

---

