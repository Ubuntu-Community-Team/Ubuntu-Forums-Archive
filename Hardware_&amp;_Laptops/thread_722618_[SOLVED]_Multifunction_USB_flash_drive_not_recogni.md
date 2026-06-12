---
title: "[SOLVED] Multifunction USB flash drive not recognized"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by nowhere@cox.net on 2008-03-12
Hi all,

I have a USB evdo modem with a builtin microSD flash slot. It's the Novatel U727. This multifunction device has a CDROM emulation with the windows and Mac drivers on it that must be mounted and then unmounted to switch the device to modem / mass storage mode. This works fine and after recompiling airprime driver with the vendor and product code added to the source, I can connect brilliantly to the internet.

Problem is that the flash drive is not accessible. It does not show at all in the fdisk -l list so there is no device attached. dmesg shows something interesting:

```
[   42.533088] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'SMB Lite v3.10.011', timestamp 2007/08/24 18:22 (1e5c)
[   48.982316] usb 2-1: USB disconnect, address 4
[   48.984250] scsi 4:0:0:0: [sr1] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   48.984263] end_request: I/O error, dev sr1, sector 64
[   48.984269] Buffer I/O error on device sr1, logical block 16
[   48.984287] scsi 4:0:0:0: [sr1] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[   48.984294] end_request: I/O error, dev sr1, sector 68
[   48.984300] Buffer I/O error on device sr1, logical block 17
[   48.986198] scsi 4:0:0:0: rejecting I/O to dead device
[   48.986207] Buffer I/O error on device sr1, logical block 16
[   48.986213] Buffer I/O error on device sr1, logical block 17
[   48.986781] scsi 4:0:0:0: rejecting I/O to dead device
[   49.126847] python[9094]: segfault at 0000000000000000 rip 00002b92e3d881c4 rsp 00007fffce4c3f50 error 4
[   50.280508] usb 2-1: new full speed USB device using uhci_hcd and address 5
[   50.450435] usb 2-1: configuration #1 chosen from 1 choice
[   50.453342] airprime 2-1:1.0: airprime converter detected

```

You can clearly see the mount of the fake CD and the unmount, then there are some errors which look like an attempt to add the flash drive, then the airprime driver finds the modem and it connects fine.

Anyone know what these errors are and how to fix them?

Thanks,
Eric

---

### Post by nowhere@cox.net on 2008-03-12
Woop, I figured it out. For those that need the info

remove the airprime driver
```
sudo modprobe -r airprime
```
then remove the usbserial driver
```
sudo modprobe -r usbserial
```
then add the usbserial driver back with the vendor and product code of your device. For me this was:
```
sudo modprobe usbserial vendor=0x1410 product=0x4100
```
then add the airprime driver
```
sudo modprobe airprime
```

Then I insert the device, the CDROM pops up, and I eject it at which point the modem is visible to airprime and the microSD card auto-mounts.  I am also using the modem right now to post and ran some speed tests and indeed the higher speed of airprime is maintained. dmesg also reports that airprime is connecting to the modem.

I plan to add the modprobes of the usbserial to a startup script. Anyone know where I can do this to get it in before airprime loads or should I just do my entire process above in rc.local or something?

Thanks,

Eric

---

