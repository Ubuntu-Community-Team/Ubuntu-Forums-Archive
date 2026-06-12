---
title: "Icy Box Usb3 hdd dock not working on usb3 ports in ubuntu"
date: 2019-07-13
forum: Hardware
---

### Post by svennils on 2019-07-13
Hi,

i've run into a strange case with my Icy Box usb3 sata disk enclosure. 

This one: [https://www.raidsonic.de/en/standards/searchresults.php?we_objectID=2022](https://www.raidsonic.de/en/standards/searchresults.php?we_objectID=2022)

It works fine on windows machines, with one or two drives inserted. 

On ubuntu, it works if and only if i use a usb2 cable (or plug it into a usb2 port).
Albeit a bit slow since i use it for cloning or backing up disks. 
Same result with a different pc, tried 3 machines. Always been like this, i just recently thought i'd get to the bottom of it.

Here is a dmesg from ubuntu 16.04, updated. Tried with ubuntu 18.04.2, no difference.


Plugged in using USB3 cable in usb3 port
dmesg:
```
[60058.218113] usb 4-2: new SuperSpeed USB device number 9 using xhci_hcd
[60058.241274] usb 4-2: device descriptor read/8, error -71
[60058.342864] usb 4-2: new SuperSpeed USB device number 9 using xhci_hcd
[60058.369653] usb 4-2: device descriptor read/8, error -71
[60063.666240] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[60068.881657] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[60069.085592] usb 4-2: device not accepting address 10, error -62
[60069.109651] usb usb4-port2: attempt power cycle
[60075.009156] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[60080.224103] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[60080.428074] usb 4-2: device not accepting address 11, error -62
[60085.631420] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[60090.846724] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[60091.050591] usb 4-2: device not accepting address 12, error -62
[60091.074699] usb usb4-port2: unable to enumerate USB device
```

Then plugged in using USB2 cable in same port

```
[60147.469989] usb 3-2: new high-speed USB device number 18 using xhci_hcd
[60147.606062] usb 3-2: New USB device found, idVendor=067b, idProduct=2773
[60147.606066] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[60147.606068] usb 3-2: Product: ATAPI-6 Bridge Controller
[60147.606070] usb 3-2: Manufacturer: Prolific Technology Inc.
[60147.606072] usb 3-2: SerialNumber: 0123456789000000005
[60147.606978] usb-storage 3-2:1.0: USB Mass Storage device detected
[60147.607366] scsi host7: usb-storage 3-2:1.0
[60148.606739] scsi 7:0:0:0: Direct-Access     Hitachi  HTS725032A9A364  PC3O PQ: 0 ANSI: 0
[60148.608505] sd 7:0:0:0: [sdc] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[60148.608524] sd 7:0:0:0: Attached scsi generic sg2 type 0
[60148.608813] sd 7:0:0:0: [sdc] Write Protect is off
[60148.608823] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[60148.609074] sd 7:0:0:0: [sdc] No Caching mode page found
[60148.609082] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[60148.630903]  sdc: sdc1
[60148.632265] sd 7:0:0:0: [sdc] Attached SCSI disk
[60149.348968] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
```


Anyone got an idea about what is going on, or what else i can check? Tried googling a bit about the device descriptor read error, or the device not accepting adress, nothing recent showing up. Just old posts about kernel problems on usb devices from 2014.

---

### Post by DuckHook on 2019-07-14
USB 3.x support on Linux is rather spotty. I have the same problem with a powered USB 3.1 hub: some devices are recognized; others are not. It's frustrating, but is often a result of the community having to reverse-engineer drivers for peripherals designed by OEMs that make sure they work with Windows but couldn't care less about Linux. Since the specs for these peripherals are usually proprietary as well, or they have quirks designed into them to accommodate Windows and therefore must actually depart from the USB standards, these become even more ornery to Linux devs.

I honestly don't know if the above is even true in your case; I'm just citing a known issue.

You are clearly logging errors in your USB 4-2 interface. What they mean, I haven't the foggiest.

---

