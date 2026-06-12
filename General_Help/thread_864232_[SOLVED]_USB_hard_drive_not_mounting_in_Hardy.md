---
title: "[SOLVED] USB hard drive not mounting in Hardy"
date: 2008-07-19
forum: General Help
---

### Post by sites on 2008-07-19
I just replaced my laptop harddrive.  The old one works just fine & it had Hardy installed on it.  The root & home partitions are ext3.  I installed Hardy on the new drive & I'm typing from it now.  Here's the problem....

Connecting the old hd by usb, it doesn't mount.  It shows up in Nautilus, but "Can't mount file" is the error that displays.  Gparted doesn't even show this drive.

'fdisk -l' only reveals the internal drive.

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008c4c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         996     8000338+  82  Linux swap / Solaris
/dev/sda2   *         997        2433    11542702+  83  Linux
/dev/sda3            2434        7296    39062047+  83  Linux


How do i mount my old Hardy drive?

---

### Post by spiderbatdad on 2008-07-19
usbmount from synaptic package manager might help you.

---

### Post by sites on 2008-07-19
no... this isn't me being lazy & not wanting to mount the drive myself.


usbmount doesn't help

but thanks =)

---

### Post by spiderbatdad on 2008-07-19
have you tried a cold plug?
Shutdown plug in the drive and boot.

Also try plugging in with system booted and run dmesg | tail

From a cold boot you might look through dmesg to get a clue.```
dmesg > ~/Destop/dmesg.txt
```

---

### Post by sites on 2008-07-19
~$ dmesg | grep -i usb

blah blah blah... ok here's the interesting part

address 3
[   31.283375] usb 2-1: configuration #1 chosen from 1 choice
[   31.286061] usbcore: registered new interface driver libusual
[   31.294643] Initializing USB Mass Storage driver...
[   31.308003] scsi2 : SCSI emulation for USB Mass Storage devices
[   31.312114] usbcore: registered new interface driver usb-storage
[   31.312118] USB Mass Storage support registered.
[   31.312242] usb-storage: device found at 3
[   31.312243] usb-storage: waiting for device to settle before scanning
[   36.265794] usb-storage: device scan complete

Without the drive the only difference is the last line.

[  293.090861] usb 5-5: USB disconnect, address 3

---

### Post by sites on 2008-07-20
What a disaster!  I took this drive out & now it just doesn't work anymore.  I put it back in the laptop & a drive error is the first thing on the screen.

I guess I can call this one solved.:(

---

