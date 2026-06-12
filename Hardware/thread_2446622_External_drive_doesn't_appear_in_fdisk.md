---
title: "External drive doesn't appear in fdisk"
date: 2020-07-03
forum: Hardware
---

### Post by grzes314 on 2020-07-03
I'm trying to mount an external drive to my Ubuntu 18.04 laptop.

After plugging it in to an USB port something appears in `dmesg`:
```
[15352.253687] usb 2-3: new SuperSpeed Gen 1 USB device number 4 using xhci_hcd
[15352.274545] usb 2-3: New USB device found, idVendor=357d, idProduct=7788, bcdDevice= 1.14
[15352.274547] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[15352.274548] usb 2-3: Product: USB to ATA/ATAPI Bridge
[15352.274549] usb 2-3: Manufacturer: JMicron
[15352.274550] usb 2-3: SerialNumber: 7380741B
[15352.276489] usb 2-3: UAS is blacklisted for this device, using usb-storage instead
```
Also, I see a new entry in `lsusb`:
```
Bus 002 Device 004: ID 357d:7788 Sharkoon QuickPort XT
```
However, nothing new appears when I run `sudo fdisk -l` or `ls /dev`.

The drive worked just fine when I last used it a few weeks ago. Maybe an update messed something up? Thanks for your suggestions :)

---

### Post by TheFu on 2020-07-05
Do you see anything like this:
```
[19162.509670]  sdc: sdc1
[19162.515474] sd 16:0:0:0: [sdc] Attached SCSI disk
[31970.993383] sd 16:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/233 GiB)
[31970.996449] sd 16:0:0:0: [sdc] Write Protect is off
[31970.996451] sd 16:0:0:0: [sdc] Mode Sense: 34 00 00 00
[31970.999447] sd 16:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[31971.028318]  sdc: sdc1
[31971.034437] sd 16:0:0:0: [sdc] Attached SCSI disk
[54350.633556]  sdc: sdc1
```
at the bottom of **dmesg** a few seconds after the USB disk is connected?
One of my USB ports doesn't seem to trigger the "new disk" stuff, but the other one, actually connected to the same USB plug on the motherboard does. I don't know why.

---

### Post by grzes314 on 2020-07-07
@TheFu
No, nothing like this appears in **dmesg**.

I don't think this is an issue with USB port, because I have also another drive that is automatically mounted without any problem. The difference between these two drives is that the one that works is formatted as ext4, and the one that doesn't work is ntfs.

The problem is also not the disk itself, because I tried plugging it into a Windows machine and it worked fine.

---

### Post by tea for one on 2020-07-07
Perhaps the ntfs file system is damaged and Ubuntu doesn't mount it to prevent further corruption.

Pop it into your Windows PC and run the check and repair file system utility.

Add or remove a file to double check it's OK. 

Then, **safely remove** the drive and see if Ubuntu is a bit happier.

---

