---
title: "Kinect devices disappearing"
date: 2012-04-05
forum: Hardware
---

### Post by demmeln on 2012-04-05
Hi,

I'm running Ubuntu 11.10 x64 on a Thinkpad T420 and I'm having trouble to connect a Kinect.

A couple of weeks ago connecting a Kinect and using it seemed to work fine. I have no idea what it was that changed and made it not work.

What happens is that when I plug in the Kinect, all 4 devices show up on lsusb (USB Hub, Motor, Audio, Video), but after one or two seconds the Audio and the Video disappear again. I have tried to reinstall various kinect related packages, but nothing has seemed to affect this at all. I even booted Oneiric from a USB stick and found that without additional packages installed the Kinect devices show up fine (and do not disappear). This makes me believe that there is something flaky with the USB configuration or some USB related kernel module. However I have no idea about those and I don't even know where to start.

Here is the output of dmesg for pluging in the Kinect. Notice the devices disappearing.

```

[ 2258.404903] usb 1-1.1: new high speed USB device number 12 using ehci_hcd
[ 2258.498898] hub 1-1.1:1.0: USB hub found
[ 2258.499082] hub 1-1.1:1.0: 3 ports detected
[ 2259.318524] usb 1-1.1.2: new full speed USB device number 13 using ehci_hcd
[ 2260.850847] usb 1-1.1.1: new high speed USB device number 14 using ehci_hcd
[ 2261.964104] usb 1-1.1.1: usbfs: USBDEVFS_CONTROL failed cmd mtp-probe rqt 128 rq 6 len 1024 ret -110
[ 2262.383049] usb 1-1.1.3: new high speed USB device number 15 using ehci_hcd
[ 2264.720928] usb 1-1.1.1: USB disconnect, device number 14
[ 2264.857543] usb 1-1.1.3: USB disconnect, device number 15

```Ah yeah I have tried with different Kinects and they are all the same.

How could I investigate this further?

Best regards,
Niko

---

