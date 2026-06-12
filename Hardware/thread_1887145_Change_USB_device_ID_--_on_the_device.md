---
title: "Change USB device ID -- on the device"
date: 2011-11-26
forum: Hardware
---

### Post by blurpo on 2011-11-26
I've been searching for ways to change the vendor ID an/or product ID (VID/PID) of my USB device (an external disk), but I can't find what I need to do. I basically find one of two things:

Either: [How to]("http://ubuntuforums.org/showthread.php?t=1381821") link a new VID/PID to the list of supported devices of a given driver

Or: [How to]("https://help.ubuntu.com/community/RenameUSBDrive") make a new USB disk show up with a label of your choosing

I want to connect these disks (two identical ones) to a Buffalo Linkstation Pro NAS (model LS-500GL). It doesn't see them though and my guess is that it doesn't recognize the VID/PID of the disks. (It runs some kind of modified Linux inside on an ARM processor if I've understood correctly.) The Linkstation doesn't offer SSH or anything, so I can't go in and play with the configuration. I suppose I would have to wait for a firmware update, but the last update was in 2007, so I'm not optimistic. (I could have concluded that the update is around the corner, but I'm not optimistic you see.)

What I would like to do is make a change to the **drives** to change the VID/PID that they report. I would change it to something generic so that the Linkstation recognizes it automatically.

Is that possible from the USB interface of the disk, or is this hard-wired inside? If this is what it takes, I also wouldn't mind cracking open the disk and flip a few jumpers, but I don't know whether such jumpers even exist.

I found [usb_modeswitch]("http://manpages.ubuntu.com/manpages/lucid/man1/usb_modeswitch.1.html") but I think it only applies to specific devices.

I don't think this is really relevant here but the disk is reported by lsusb as:
```
Bus 001 Device 009: ID 1058:1021 Western Digital Technologies, Inc.
```
And I'm using Ubuntu 10.04.

Many thanks in advance!

---

