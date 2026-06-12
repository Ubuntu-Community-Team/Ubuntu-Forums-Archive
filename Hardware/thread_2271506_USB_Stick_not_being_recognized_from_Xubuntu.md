---
title: "USB Stick not being recognized from Xubuntu"
date: 2015-03-30
forum: Hardware
---

### Post by jess10 on 2015-03-30
I have adquired a new USB storage and it has been formatted  with FAT32 format. I tried to change the format of the device and it  failed in the middle of the process and then I can't format the device.  When I use **fdisk -l** command, it doesn't appears. The only way in which I can see it is using the following command: **ls -la /dev/disk/by-id/**

  ```
...
lrwxrwxrwx 1 root root   9 mar 30 20:43 usb-Generic_USB_Flash_Disk-0:0 -> ../../sdc
...
```

I am not being able to mount the device and gparted not recognized  it. I have been surfing on Internet during hours but I can't find a  solution.

  Thanks in advance.

---

### Post by weatherman2 on 2015-03-30
Unplug the drive, then plug it back in again.  Type this terminal command:

```
dmesg
```

Look at the end of the results - anything related to USB devices?

And what do you get when (with USB device plugged in) you type this terminal command:

```
lsusb
```

?

---

### Post by jess10 on 2015-03-31
**dmesg**

```
[   51.610172] usb 3-2: new high-speed USB device number 5 using xhci_hcd
[   51.739959] usb 3-2: New USB device found, idVendor=058f, idProduct=1234
[   51.739963] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   51.739965] usb 3-2: Product: Mass Storage Device
[   51.739966] usb 3-2:** Manufacturer: Alcor Micro**
[   51.740476] usb-storage 3-2:1.0: USB Mass Storage device detected
[   51.740554] scsi7 : usb-storage 3-2:1.0
[   52.739066] scsi 7:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 4
[   52.739363] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   52.740508] sd 7:0:0:0: [sdc] Attached SCSI removable disk
```

**lsusb**

```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0cf3:3004 Atheros Communications, Inc. 
**Bus 003 Device 005: ID 058f:1234 Alcor Micro Corp. Flash Drive**
Bus 003 Device 002: ID 0bda:58b9 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

