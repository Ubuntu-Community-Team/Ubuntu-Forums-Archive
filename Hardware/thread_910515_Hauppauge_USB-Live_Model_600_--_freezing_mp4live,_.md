---
title: "Hauppauge USB-Live Model 600 -- freezing mp4live, black screen"
date: 2008-09-04
forum: Hardware
---

### Post by _UsUrPeR_ on 2008-09-04
I have been scratching my head about this all day. I am trying to get a USB video grabber working with Ubuntu 8.04 for a while now with no success.

Here's the general info:
```

lsusb --

Bus 002 Device 002: ID 0573:2d01 Zoran Co. Personal Media Division (Nogatech) Hauppauge USB-Live Model 600
```
```

dmesg --

[ 2943.544168] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 2941.618895] usb 1-1: configuration #1 chosen from 4 choices
[ 2941.620758] usbvision_probe: Hauppauge WinTV USB Live Pro (NTSC M/N) found
[ 2941.620819] USBVision[1]: registered USBVision Video device /dev/video0 [v4l2]
[ 2941.620860] USBVision[1]: registered USBVision VBI device /dev/vbi0 [v4l2] (Not Working Yet!)
[ 2942.006532] saa7115 0-0025: saa7113 found (1f7113d0e100000) @ 0x4a (usbvision #0)
```

Using mp4Live, the program appears to detect the USB device, and also detects the S-Video and Composite Video Input portions of the device, but after plugging in a device to the composite input, there is no image. Switching between NTSC, PAL, and SECAM has no effect.

I have had mp4Live running properly on the same computer with the following device:
```

lsusb --
Bus 005 Device 005: ID eb1a:2820 eMPIA Technology, Inc.
```

Unfortunately, that device is no longer available for purchase, and I have to make do with another one.

Any help would be greatly appreciated.

For reference, I have tried the suggestions [here]("http://ubuntuforums.org/showthread.php?t=566868&highlight=0573%3A2d01"). Unfortunately, there was no positive result.

---

