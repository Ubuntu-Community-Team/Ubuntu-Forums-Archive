---
title: "Empia Easier Cap Video issue"
date: 2017-03-02
forum: Hardware
---

### Post by betchern0t on 2017-03-02
Yes yet another clone of EasyCap...

This is a USB dongle containing an EM2860 and SAA7113h - pulled the cover off and had a look. The em28xx driver recognises this as a em2860/SAA711x reference design and assigns it as card 19.

I have a camera from Security Cam 2000. I plug it into a composite port on a tv and it works fine. So I am thinking the problem is either the USB dongle or drivers.

There is nothing in the kernel log jumping out saying there is a problem:

```

Mar  2 21:01:42 nimrod kernel: [ 8129.756684] usb 1-1.4.4: new high-speed USB device number 8 using xhci_hcd
Mar  2 21:01:42 nimrod kernel: [ 8129.857018] usb 1-1.4.4: New USB device found, idVendor=eb1a, idProduct=2861
Mar  2 21:01:42 nimrod kernel: [ 8129.857026] usb 1-1.4.4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Mar  2 21:01:42 nimrod kernel: [ 8129.857822] em28xx: New device   @ 480 Mbps (eb1a:2861, interface 0, class 0)
Mar  2 21:01:42 nimrod kernel: [ 8129.857829] em28xx: Video interface 0 found: isoc
Mar  2 21:01:42 nimrod kernel: [ 8129.857860] em28xx: chip ID is em2860
Mar  2 21:01:43 nimrod kernel: [ 8129.949199] em2860 #0: board has no eeprom
Mar  2 21:01:43 nimrod kernel: [ 8130.008728] em2860 #0: No sensor detected
Mar  2 21:01:43 nimrod kernel: [ 8130.015614] em2860 #0: found i2c device @ 0x4a on bus 0 [saa7113h]
Mar  2 21:01:43 nimrod kernel: [ 8130.031508] em2860 #0: Your board has no unique USB ID.
Mar  2 21:01:43 nimrod kernel: [ 8130.031516] em2860 #0: A hint were successfully done, based on i2c devicelist hash.
Mar  2 21:01:43 nimrod kernel: [ 8130.031520] em2860 #0: This method is not 100% failproof.
Mar  2 21:01:43 nimrod kernel: [ 8130.031522] em2860 #0: If the board were missdetected, please email this log to:
Mar  2 21:01:43 nimrod kernel: [ 8130.031524] em2860 #0: 	V4L Mailing List  <linux-media@vger.kernel.org>
Mar  2 21:01:43 nimrod kernel: [ 8130.031527] em2860 #0: Board detected as EM2860/SAA711X Reference Design
Mar  2 21:01:43 nimrod kernel: [ 8130.108680] em2860 #0: Identified as EM2860/SAA711X Reference Design (card=19)
Mar  2 21:01:43 nimrod kernel: [ 8130.108688] em2860 #0: analog set to isoc mode.
Mar  2 21:01:43 nimrod kernel: [ 8130.109018] em2860 #0: Registering V4L2 extension
Mar  2 21:01:43 nimrod mtp-probe: checking bus 1, device 8: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1.4/1-1.4.4"
Mar  2 21:01:43 nimrod mtp-probe: bus: 1, device: 8 was not an MTP device
Mar  2 21:01:43 nimrod rtkit-daemon[2227]: Supervising 3 threads of 1 processes of 1 users.
Mar  2 21:01:43 nimrod rtkit-daemon[2227]: Successfully made thread 7304 of process 2226 (n/a) owned by '1000' RT at priority 5.
Mar  2 21:01:43 nimrod rtkit-daemon[2227]: Supervising 4 threads of 1 processes of 1 users.
Mar  2 21:01:43 nimrod colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Mar  2 21:01:43 nimrod kernel: [ 8130.493002] saa7115 4-0025: saa7113 found @ 0x4a (em2860 #0)
Mar  2 21:01:44 nimrod kernel: [ 8131.268761] em2860 #0: Config register raw data: 0x10
Mar  2 21:01:44 nimrod kernel: [ 8131.292721] em2860 #0: AC97 vendor ID = 0x83847652
Mar  2 21:01:44 nimrod kernel: [ 8131.304717] em2860 #0: AC97 features = 0x6a90
Mar  2 21:01:44 nimrod kernel: [ 8131.304724] em2860 #0: Sigmatel audio processor detected (stac 9752)
Mar  2 21:01:46 nimrod kernel: [ 8133.704970] em2860 #0: V4L2 video device registered as video0
Mar  2 21:01:46 nimrod kernel: [ 8133.704973] em2860 #0: V4L2 VBI device registered as vbi0
Mar  2 21:01:46 nimrod kernel: [ 8133.704975] em2860 #0: V4L2 extension successfully initialized
Mar  2 21:01:46 nimrod kernel: [ 8133.710044] em2860 #0: Registering snapshot button...
Mar  2 21:01:46 nimrod kernel: [ 8133.710106] input: em28xx snapshot button as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1.4/1-1.4.4/input/input21
Mar  2 21:01:46 nimrod kernel: [ 8133.710234] em2860 #0: Remote control support is not available for this card.
Mar  2 21:01:46 nimrod kernel: [ 8133.710237] em28xx: Registered (Em28xx Input Extension) extension

```

when run with something like cheese I get a screen full of static. VLC just shows the iconic traffic cone. 

lsusb:

```

Bus 002 Device 004: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 003: ID 125f:a15a A-DATA Technology Co., Ltd. DashDrive Durable HD710 portable HDD various size
Bus 002 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID eb1a:2861 eMPIA Technology, Inc. 
Bus 001 Device 005: ID 264a:3004  
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 002: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have upgrade to the latest kernel for my version of linux as well as the latest version of the os (Ubuntu 16.04 based):

```

paulc@nimrod ~ $ uname -r
4.4.0-64-generic
paulc@nimrod ~ $ 

```

I checked on git for the latest version of the drivers but there have been no commits for the last 3 or 4 years and so I have not compiled a new copy. Most of the issues on the internet like this are also 3-4 years old.

I haven't done much with video etc. I am hoping that someone will chime in with a comment that says I have missed something simple like not set it up correctly - standard, resolution or sync speed.

Any suggestions to fix this or to find the problem would be greatly appreciated.

Cheers Paul

---

