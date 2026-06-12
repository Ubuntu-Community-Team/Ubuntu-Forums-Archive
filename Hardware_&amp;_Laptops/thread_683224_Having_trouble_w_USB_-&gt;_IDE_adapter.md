---
title: "Having trouble w/ USB -&gt; IDE adapter"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by shaggy999 on 2008-01-30
I'm having a lot of trouble trying to get a new USB2.0 -> IDE adapter to work. My previous external hard drive broke (the connector shattered and pins went everywhere), so I decided to go a bit more basic because I have 6 different drives I hook it up to (3 WD 120 GB Special Edition & 3 250 GB WD Special Edition). Anyway, the manufacturer said Windows/MacOS support, but I figured it would work in Linux as well. And it does, sort of. Actually this device is extremely finicky and only works about 10% of the time and it doesn't matter if it's on Windows or Linux. I was actually able to get one of my drives connected and working for a little while and I was reading and writing to it in Linux, but trying to get it "just right" doesn't seem to be easy.

My problem is that I plug the adapter into the drive and the usb cable into the computer and nothing happens! Well, 90% of the time nothing happens. The other 10% of the time it works flawlessly. It's got to be something I'm doing but I don't know how to troubleshoot! In windows I go into the device manager and watch for the device and I can hear Windows when I plug in and unplug the device. I'm not sure where to go in Linux to see real-time changes. And is there a command to force linux to check for new usb hardware?

I got another drive all set up with an ext3 partition but then didn't know how to mount it, so I decided to reboot my computer (nothing was disconnected) and when I come back the drive is gone! Even the partition editor can't see it!

When it can be seen it shows up as /dev/sdb

Any thoughts?

---

### Post by shaggy999 on 2008-01-30
Ok, I found some more info in /var/log/syslog

```
Jan 30 16:47:49 gutsy-laptop kernel: [ 1699.824000] usb 5-5: new high speed USB device using ehci_hcd and address 13
Jan 30 16:47:49 gutsy-laptop NetworkManager: <debug> [1201740469.633435] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial'). 
Jan 30 16:47:49 gutsy-laptop kernel: [ 1699.956000] usb 5-5: configuration #1 chosen from 1 choice
Jan 30 16:47:49 gutsy-laptop kernel: [ 1700.048000] scsi12 : SCSI emulation for USB Mass Storage devices
Jan 30 16:47:49 gutsy-laptop kernel: [ 1700.048000] usb-storage: device found at 13
Jan 30 16:47:49 gutsy-laptop kernel: [ 1700.048000] usb-storage: waiting for device to settle before scanning
Jan 30 16:47:49 gutsy-laptop NetworkManager: <debug> [1201740469.794620] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0'). 
Jan 30 16:47:49 gutsy-laptop NetworkManager: <debug> [1201740469.861031] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_usbraw'). 
Jan 30 16:47:54 gutsy-laptop kernel: [ 1705.048000] usb-storage: device scan complete
Jan 30 16:48:00 gutsy-laptop kernel: [ 1710.828000] usb 5-5: USB disconnect, address 13
Jan 30 16:48:00 gutsy-laptop kernel: [ 1710.828000] scsi 12:0:0:0: scsi: Device offlined - not ready after error recovery
Jan 30 16:48:00 gutsy-laptop NetworkManager: <debug> [1201740480.526980] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_if0'). 
Jan 30 16:48:00 gutsy-laptop NetworkManager: <debug> [1201740480.527327] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial_usbraw'). 
Jan 30 16:48:00 gutsy-laptop NetworkManager: <debug> [1201740480.527527] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_702_noserial'). 
```

---

### Post by shaggy999 on 2008-01-30
Ok, I made some progress, but now I'm really confused. The company that makes the adapter recommends setting the hard drive to master, which I originally had.done. But I tried switching them to "cable select". Now the drives are detected and mounted no problem. But when I start writing data to the drive it locks up and I get this error in the logs:

```
 kernel: [  538.552000] usb 5-7: reset high speed USB device using ehci_hcd and address 4
```

The address number changes each time.

---

