---
title: "UMTS USB Stick Novatel MC950D - Problem"
date: 2008-11-06
forum: Hardware
---

### Post by darios54 on 2008-11-06
I try to use my Novatel MC950D 3G USB Stick on Ubuntu 8.10. After
inserting the stick Ubuntung recognized the stick as an USB storage and prints some errors

/var/syslog
```
Nov  3 14:10:24 santos kernel: [  125.060198] usb 3-1: new full speed USB device using uhci_hcd and address 2
Nov  3 14:10:24 santos kernel: [  125.235036] usb 3-1: configuration #1 chosen from 1 choice
Nov  3 14:10:24 santos kernel: [  125.415116] usbcore: registered new interface driver libusual
Nov  3 14:10:24 santos kernel: [  125.431692] Initializing USB Mass Storage driver...
Nov  3 14:10:24 santos kernel: [  125.433322] scsi2 : SCSI emulation for USB Mass Storage devices
Nov  3 14:10:24 santos kernel: [  125.434425] usbcore: registered new interface driver usb-storage
Nov  3 14:10:24 santos kernel: [  125.435327] USB Mass Storage support registered.
Nov  3 14:10:24 santos kernel: [  125.436179] usb-storage: device found at 2
Nov  3 14:10:24 santos kernel: [  125.436184] usb-storage: waiting for device to settle before scanning
Nov  3 14:10:29 santos kernel: [  130.437318] usb-storage: device scan complete
Nov  3 14:10:29 santos kernel: [  130.440293] scsi 2:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
Nov  3 14:10:30 santos kernel: [  130.498035] sr1: scsi-1 drive
Nov  3 14:10:30 santos kernel: [  130.498365] sr 2:0:0:0: Attached scsi CD-ROM sr1
Nov  3 14:10:30 santos kernel: [  130.498672] sr 2:0:0:0: Attached scsi generic sg2 type 5
Nov  3 14:10:30 santos kernel: [  130.702247] sr1: CDROM (ioctl) error, command: Get event status notification 4a 01 00 00 10 00 00 00 08 00
Nov  3 14:10:30 santos kernel: [  130.702272] sr: Sense Key : No Sense [current] 
Nov  3 14:10:30 santos kernel: [  130.702278] sr: Add. Sense: No additional sense information
Nov  3 14:10:30 santos kernel: [  130.873236] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00

```

lsusb shows the device as follows
```
BUS 003 Device 002: ID 1410:5010 Novatel Wireless
```

after ejecting the device with
```
sudo eject /dev/scd1
```

lsusb shows the device as follows
```
BUS 003 Device 003: ID 1410:4400 Novatel Wireless
```

After that I can use the stick as an UMTS modem and everything works well with the new network manager.

Is there any possibility to get this fixed? I do not want to eject the device everytime again.

---

### Post by darios54 on 2008-11-07
nobody outside in the world having an idea??? :(

---

### Post by nhoeller on 2009-03-24
I assume you resolved your problem, but if not, I installed the most recent usb_modeswitch ([http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)) and created a file file called **91-usb_modeswitch.rules** in **/etc/udev/rules.d** containing

[INDENT]SUBSYSTEM=="usb", SYSFS{idProduct}=="5010",  SYSFS{idVendor}=="1410", RUN+="/usr/sbin/usb_modeswitch"[/INDENT]

I also edited **/etc/usb_modeswitch.conf** and removed the semicolons in front of all of the lines relating to the MC950D.

Now when I boot the Linux server or plug the MC950D, **usb_modeswitch** is called automatically to release the ZeroCD.  I can then invoke **wvdial**, a step I still need to automate.

---

