---
title: "usb port problem"
date: 2015-02-10
forum: Hardware
---

### Post by okkadiroglu on 2015-02-10
Hi.

I am using Ubuntu14.10 on a AMD64 comp. An extension cable, 1 ~ 1.5m long, connected to the USB3.0 port of my desktop computer allows me to connect USB sticks and hard disks to the system by plugging them to this extension cable on my desk. Everything works well after I am finished using it I umount the device properly . Next time when I try to connect a device to this port nothing happens, I can not see the device with lsusb. If I reboot the computer then I can use the USB port. What is going on how can I reset a particular USB port?

Best regards

---

### Post by justananomaly on 2015-02-10
What are the USB settings in your BIOS?

---

### Post by Yellow Pasque on 2015-02-10
Do you see any relevant information in dmesg when you try to reconnect the device and it fails?
```
dmesg | tail -n 20
```

If you disconnect/reconnect the extension cable before plugging in the device, does it then work properly?

Can you show lsusb?
```
sudo update-usbids
sudo lsusb -t
```

---

### Post by okkadiroglu on 2015-02-11
Hi,

Thanks for the help. I connected two hard disks (USB2.0 and USB3.0) with extension chords to my computer. lsusb, dmesg results are in lsusb2d.txt and dmesg2d.txt. I can see both disks. Then I umount both disks (lsusb0d.txt, dmesg0d.txt). Connected them again  but I can see only the USB2.0 disk. (lsusb2dx.txt, dmesg2dx.txt). I used updat-usbid but nothing happened.

---

### Post by okkadiroglu on 2015-02-11
One more file

---

### Post by Yellow Pasque on 2015-02-11
update-usbids just makes things (a bit) more human-readable.
Putting the info all together for me to see easier:

Before you plug anything in:
```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 093a:2516 Pixart Imaging, Inc. 
Bus 004 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Plugged in:
```
Bus 003 Device 003: ID 1058:1010 Western Digital Technologies, Inc. Elements Portable (WDBAAR)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 093a:2516 Pixart Imaging, Inc. 
Bus 004 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 04e8:61b6 Samsung Electronics Co., Ltd M3 Portable Hard Drive 1TB
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[  510.829831] usb 3-4: new high-speed USB device number 3 using ehci-pci
[  510.967392] usb 3-4: New USB device found, idVendor=1058, idProduct=1010
[  510.967396] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  510.967398] usb 3-4: Product: External HDD    
[  510.967399] usb 3-4: Manufacturer: Western Digital 
[  510.967401] usb 3-4: SerialNumber: 57442D575843314531314C52393539
[  511.017897] usb-storage 3-4:1.0: USB Mass Storage device detected
[  511.018016] scsi6 : usb-storage 3-4:1.0
[  511.018191] usbcore: registered new interface driver usb-storage
[  511.040436] usbcore: registered new interface driver uas
[  511.426740] usb 8-1: new high-speed USB device number 2 using xhci_hcd
[  511.610201] usb 8-1: New USB device found, idVendor=04e8, idProduct=61b6
[  511.610204] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  511.610207] usb 8-1: Product: Samsung M3 Portable
[  511.610208] usb 8-1: Manufacturer: Samsung M3 Portable
[  511.610210] usb 8-1: SerialNumber: EDF37DE909000013
[  511.611384] usb-storage 8-1:1.0: USB Mass Storage device detected
[  511.611533] scsi7 : usb-storage 8-1:1.0
[  512.020617] scsi 6:0:0:0: Direct-Access     WD       5000BEV External 1.75 PQ: 0 ANSI: 4
[  512.021015] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  512.022331] sd 6:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  512.022954] sd 6:0:0:0: [sdb] Write Protect is off
[  512.022958] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  512.023579] sd 6:0:0:0: [sdb] No Caching mode page found
[  512.023583] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  512.044805]  sdb: sdb1
[  512.048004] sd 6:0:0:0: [sdb] Attached SCSI disk
[  512.613241] scsi 7:0:0:0: Direct-Access     Samsung  M3 Portable      1301 PQ: 0 ANSI: 6
[  512.614095] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  512.619805] sd 7:0:0:0: [sdc] Spinning up disk...
[  513.622342] .ready
[  513.622586] sd 7:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[  513.622870] sd 7:0:0:0: [sdc] Write Protect is off
[  513.622877] sd 7:0:0:0: [sdc] Mode Sense: 33 00 00 08
[  513.623156] sd 7:0:0:0: [sdc] No Caching mode page found
[  513.623161] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  513.653014]  sdc: sdc1
[  513.654251] sd 7:0:0:0: [sdc] Attached SCSI disk
[  797.855648] usb 3-4: USB disconnect, device number 3
[  802.852813] usb 8-1: USB disconnect, device number 2
```

Plugged in again:
```
Bus 003 Device 004: ID 1058:1010 Western Digital Technologies, Inc. Elements Portable (WDBAAR)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 093a:2516 Pixart Imaging, Inc. 
Bus 004 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[  918.282011] usb 3-4: new high-speed USB device number 4 using ehci-pci
[  918.415453] usb 3-4: New USB device found, idVendor=1058, idProduct=1010
[  918.415461] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  918.415466] usb 3-4: Product: External HDD    
[  918.415470] usb 3-4: Manufacturer: Western Digital 
[  918.415474] usb 3-4: SerialNumber: 57442D575843314531314C52393539
[  918.415951] usb-storage 3-4:1.0: USB Mass Storage device detected
[  918.416130] scsi8 : usb-storage 3-4:1.0
[  919.416353] scsi 8:0:0:0: Direct-Access     WD       5000BEV External 1.75 PQ: 0 ANSI: 4
[  919.417017] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  919.418071] sd 8:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[  919.418825] sd 8:0:0:0: [sdb] Write Protect is off
[  919.418835] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  919.419592] sd 8:0:0:0: [sdb] No Caching mode page found
[  919.419600] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  919.432375]  sdb: sdb1
[  919.434712] sd 8:0:0:0: [sdb] Attached SCSI disk

```

---

### Post by Yellow Pasque on 2015-02-11
Unfortunately, dmesg doesn't give any sort of error when you plug in the Samsung drive for the second time. I'm not sure what to suggest, but if it was me, I'd try the latest kernel. The easiest way to do that without affecting your current install is to torrent Ubuntu 15.04 and throw it on a USB stick.

---

