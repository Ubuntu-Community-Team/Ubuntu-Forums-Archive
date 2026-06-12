---
title: "iPod Touch and iPhone Fail To Mount As Cameras"
date: 2008-11-30
forum: General Help
---

### Post by pbjoiner on 2008-11-30
I'm trying to import my pics from my iPod Touch (and iPhone) to F-Spot. When I attach the iTouch F-Spot asks which device I'd like to import photos. The selections are USB and USB bus#:dev#. Neither work.

It stopped working for me after I downgraded to 8.04 32bit to get my Canon Pixma ip1800 working (which is functioning well, thank you). I suspect the changes made to get the printer working are killing the ability to mount the iTouch as a camera. I had to install libglib1.2 to satisfy the driver dependancies. I've a hunch that's relevant since some other threads elsewhere on the net mention mention libg when resolving similar issues with digital cameras. 

I've included some information below that I believe to be at least vaguely meaningful. It's not particularly helpful to me but perhaps someone with more experience might know what I'm missing.

My Seagate 8G thumbdrive and Fuji FinePix 2800 mount automatically. This appears to be Apple specific. 


lsusb:
The device connects.

Bus 002 Device 009: ID 05ac:1291 Apple Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04a9:10c2 Canon, Inc. 
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000  


dmesg:
This also looks normal.

[11421.937887] usb 2-6: new high speed USB device using ehci_hcd and address 7
[11421.997647] usb 2-6: configuration #1 chosen from 3 choices
[11592.745161] usb 1-5: new full speed USB device using ohci_hcd and address 4
[11592.838925] usb 1-5: configuration #1 chosen from 1 choice
[11592.895797] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10C2
[11592.895933] usbcore: registered new interface driver usblp
[11615.235337] usb 2-6: USB disconnect, address 7
[11617.152692] usb 2-7: new high speed USB device using ehci_hcd and address 9
[11617.212090] usb 2-7: configuration #1 chosen from 3 choices


dir /dev/usb*
There appear to be device entries (though I have no clue what any of this really means).

crw-rw---- 1 root root 254,  0 2008-11-29 16:19 /dev/usbdev1.1_ep00
crw-rw---- 1 root root 254,  1 2008-11-29 16:19 /dev/usbdev1.1_ep81
crw-rw---- 1 root root 254,  4 2008-11-29 16:19 /dev/usbdev1.2_ep00
crw-rw---- 1 root root 254,  6 2008-11-29 16:19 /dev/usbdev1.2_ep02
crw-rw---- 1 root root 254,  8 2008-11-29 16:19 /dev/usbdev1.2_ep03
crw-rw---- 1 root root 254,  5 2008-11-29 16:19 /dev/usbdev1.2_ep81
crw-rw---- 1 root root 254,  7 2008-11-29 16:19 /dev/usbdev1.2_ep82
crw-rw---- 1 root root 254,  9 2008-11-29 16:19 /dev/usbdev1.2_ep83
crw-rw---- 1 root root 254, 10 2008-11-29 16:19 /dev/usbdev1.3_ep00
crw-rw---- 1 root root 254, 11 2008-11-29 16:19 /dev/usbdev1.3_ep01
crw-rw---- 1 root root 254, 12 2008-11-29 16:19 /dev/usbdev1.3_ep82
crw-rw---- 1 root root 254, 17 2008-11-29 23:35 /dev/usbdev1.4_ep00
crw-rw---- 1 root root 254, 18 2008-11-29 23:35 /dev/usbdev1.4_ep01
crw-rw---- 1 root root 254, 19 2008-11-29 23:35 /dev/usbdev1.4_ep82
crw-rw---- 1 root root 254,  2 2008-11-29 16:19 /dev/usbdev2.1_ep00
crw-rw---- 1 root root 254,  3 2008-11-29 16:19 /dev/usbdev2.1_ep81
crw-rw---- 1 root root 254, 13 2008-11-29 23:36 /dev/usbdev2.9_ep00
crw-rw---- 1 root root 254, 14 2008-11-29 23:36 /dev/usbdev2.9_ep02
crw-rw---- 1 root root 254, 15 2008-11-29 23:36 /dev/usbdev2.9_ep81
crw-rw---- 1 root root 254, 16 2008-11-29 23:36 /dev/usbdev2.9_ep83
lrwxrwxrwx 1 root root       7 2008-11-29 23:35 /dev/usblp0 -> usb/lp0


dir /dev/sd*
No sd* device is created for the iTouch.

brw-rw---- 1 root disk 8,  0 2008-11-29 16:19 /dev/sda
brw-rw---- 1 root disk 8,  1 2008-11-29 16:19 /dev/sda1
brw-rw---- 1 root disk 8,  2 2008-11-29 16:19 /dev/sda2
brw-rw---- 1 root disk 8,  3 2008-11-29 16:19 /dev/sda3
brw-rw---- 1 root disk 8,  4 2008-11-29 16:19 /dev/sda4
brw-rw---- 1 root disk 8, 16 2008-11-29 16:19 /dev/sdb
brw-rw---- 1 root disk 8, 32 2008-11-29 16:19 /dev/sdc
brw-rw---- 1 root disk 8, 48 2008-11-29 16:19 /dev/sdd
brw-rw---- 1 root disk 8, 64 2008-11-29 16:19 /dev/sde

---

### Post by SPr on 2008-11-30
I don't have an ipod so I can't test this. In the Debian Lenny (not got Ubuntu) repos there is a program called "ipod" which from the description
> 
tool for retrieving informations from iPods 
libipoddevice provides basic low level device information about iPod devices.
The library makes it extremely easy to detect iPods. Basic metadata the
library can provide about an iPod:
 * Mount Point
 * Device Path
 * iPod Model (Regular, Shuffle, Photo)
 * iPod Name (not the volume name, but the actual user-assigned name)
 * Disk Space (size, available, used)
 sounds like something you need. Installing it may also install other dependencies you'll need.

---

### Post by pbjoiner on 2008-12-01
There are quite a few packages that deal with the iPod. I believe these libraries don't support the multi-touch devices such as iPod Touch or iPhone. The multi-touch platform is a radically different architecture from the original iPod, Shuffle, and Nano.

Selecting the iPod package installs libpoddevice0 but has no other dependencies.

That was a good idea, though. I'll troll through the rest of the available packages to see what's what.

---

### Post by fyrmedic on 2008-12-09
Here is my understanding of the iPhone/iTouch. It appears that there is no really good and reliable way to get them to work with linux. It seems that if the firmware is of the 1st generation group one can get it them to mesh but only after "jailbreaking" the device.

As far as the 2nd gen. devices, they are too new and there haven't been any really successful attempts at decoding the hash algorithms that have changed since the first gen.

I am particularly upset about this because it means that I have to use windows to update my touch and the only machine I have with windows is "ancient" and SLOW!

Good luck in your endeavour and please post any workable solutions so that we may all benefit.

Brad

---

### Post by ounas on 2008-12-10
Will just have too wait...
Then again patience is a virtue 

:guitar:

---

