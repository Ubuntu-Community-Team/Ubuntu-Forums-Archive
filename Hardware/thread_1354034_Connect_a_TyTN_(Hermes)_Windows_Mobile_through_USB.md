---
title: "Connect a TyTN (Hermes) Windows Mobile through USB"
date: 2009-12-13
forum: Hardware
---

### Post by Oceanwatcher on 2009-12-13
I am running Kubuntu 9.10, KDE 4.3.4 and this is what shows if I type lsusb in a terminal:

```
Bus 003 Device 002: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 056a:0041 Wacom Co., Ltd Intuos2 4x5
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:08c6 Logitech, Inc. QuickCam for DELL Notebooks
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 0bb4:0b04 High Tech Computer Corp. Hermes / TyTN / T-Mobile MDA Vario II / O2 Xda Trion
Bus 005 Device 002: ID 046d:0a01 Logitech, Inc. USB Headset
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

My mobile phone is a HTC TyTN (Hermes) running Windows Mobile 6 and has a 2GB memorycard. When I connect it to WindowsXP I am able to transfer files back and forth (yeah, I know Kubuntu is not Windows). At this point, I am not trying to get anything to sync with my mobile, I am just trying to get it to show up as a USB device in KDE and be able to transfer files to or from it.

Does anyone have any idea what to do?

I must also mention that I have had problems after upgrading to Kubuntu 9.10 to connect my cardreader to my laptop (it is a Dell XPS M1210) and offload my photos to my laptop. So maybe there is something wrong with handling of USB stuff?

The one thing that is still working ok is pendrives. No problem there.

---

### Post by MaindotC on 2009-12-13
Disconnect the phone from your machine.  Open up syslog, and watch for updates to syslog.  Plug in the phone - you should see syslog go crazy and type a bunch of stuff that you don't understand.  Somewhere in that output, you should see a reference to /dev/sdb or /dev/sdc or something along those lines.  That is how your phone is identified to Ubuntu.

You can take this a step further by looking at:
```

sudo fdisk -l

```

This displays all of the attached, recognizable storage devices.  You should see one that matches the capacity of your hard drive(s), and one that matches your phone.  It will tell you the partitioning information of the memory on your phone and you mount it using the mount command.

---

### Post by Oceanwatcher on 2009-12-15
Finally had some time to try your suggestions. Opened syslog and unplugged. Here is what happened:

```
2009-12-15 18:46:14	Aslan	kernel	[  477.320219] usb 5-1: USB disconnect, address 2
2009-12-15 18:46:20	Aslan	kernel	[  483.016159] usb 5-1: new full speed USB device using uhci_hcd and address 4
2009-12-15 18:46:35	Aslan	kernel	[  498.128079] usb 5-1: device descriptor read/64, error -110
2009-12-15 18:46:50	Aslan	kernel	[  513.347301] usb 5-1: device descriptor read/64, error -110
2009-12-15 18:46:51	Aslan	kernel	[  513.560132] usb 5-1: new full speed USB device using uhci_hcd and address 5
2009-12-15 18:47:06	Aslan	kernel	[  528.732163] usb 5-1: device descriptor read/64, error -110
2009-12-15 18:47:21	Aslan	kernel	[  543.948147] usb 5-1: device descriptor read/64, error -110
2009-12-15 18:47:21	Aslan	kernel	[  544.164122] usb 5-1: new full speed USB device using uhci_hcd and address 6
2009-12-15 18:47:32	Aslan	kernel	[  554.572129] usb 5-1: device not accepting address 6, error -110
2009-12-15 18:47:32	Aslan	kernel	[  554.742104] usb 5-1: new full speed USB device using uhci_hcd and address 7
2009-12-15 18:47:42	Aslan	kernel	[  565.148143] usb 5-1: device not accepting address 7, error -110
2009-12-15 18:47:42	Aslan	kernel	[  565.148176] hub 5-0:1.0: unable to enumerate USB device on port 1
```

At this point it look like it stopped. Running the command you gave me listed nothing else than the partitions on my internal harddrive.

---

### Post by MaindotC on 2009-12-15
Here's a brief idea of what's going on:
> **Oceanwatcher said:**
> 
```
2009-12-15 18:46:14	Aslan	kernel	[  477.320219] usb 5-1: USB disconnect, address 2

```
You unplugged the usb device.
```

2009-12-15 18:46:20	Aslan	kernel	[  483.016159] usb 5-1: new full speed USB device using uhci_hcd and address 4

```
You plugged it back in and your machine is trying to use the uhci_hcd module to communicate with the usb device.  I couldn't find anything on my machine about uhci_hcd nor could I find an official description of this module so it may be outdated.
```

2009-12-15 18:46:35	Aslan	kernel	[  498.128079] usb 5-1: device descriptor read/64, error -110
2009-12-15 18:46:50	Aslan	kernel	[  513.347301] usb 5-1: device descriptor read/64, error -110

```
Your machine is having difficulty reading the usb device.
[code]Running the command you gave me listed nothing else than the partitions on my internal harddrive.
Well, yes, obviously seeing as how it can't read from the device, how can it list the partition information?  Can you look at your phone and see if there's anything different you can do - maybe change a data transfer setting or try connecting it when it's powered off?

---

