---
title: "Getting Webcam Working (looks to be detected)"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by sailor420 on 2005-10-24
So I have a webcam I got on cheap somewhere a while ago. I wanted to see if it would work in Ubuntu. So, I plugged it in, but I don't even know where to start from here.

Here's what syslog has to say:

```
Oct 24 21:25:04 localhost kernel: [4296897.516000] usb 6-1: new full speed USB device using ohci_hcd and address 2
Oct 24 21:25:05 localhost kernel: [4296897.907000] Linux video capture interface: v1.00
Oct 24 21:25:05 localhost kernel: [4296897.920000] sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.24
Oct 24 21:25:05 localhost kernel: [4296897.928000] usb 6-1: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x6028)
Oct 24 21:25:05 localhost kernel: [4296898.045000] usb 6-1: PAS202BCB image sensor detected
Oct 24 21:25:05 localhost kernel: [4296898.691000] usb 6-1: Initialization succeeded
Oct 24 21:25:05 localhost kernel: [4296898.693000] usb 6-1: V4L2 device registered as /dev/video0
Oct 24 21:25:05 localhost kernel: [4296898.693000] usb 6-1: Optional device control through 'sysfs' interface ready
Oct 24 21:25:05 localhost kernel: [4296898.693000] usbcore: registered new driver sn9c102
Oct 24 21:25:05 localhost usb.agent[9667]:      sn9c102: loaded successfully
```

So it looks like it recognizes it and even has a driver for it, and assigned the device to /dev/video0.

For giggles, here's what dmesg has to say:

```
[4296897.516000] usb 6-1: new full speed USB device using ohci_hcd and address 2
[4296897.907000] Linux video capture interface: v1.00
[4296897.920000] sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.24
[4296897.928000] usb 6-1: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x6028)
[4296898.045000] usb 6-1: PAS202BCB image sensor detected
[4296898.691000] usb 6-1: Initialization succeeded
[4296898.693000] usb 6-1: V4L2 device registered as /dev/video0
[4296898.693000] usb 6-1: Optional device control through 'sysfs' interface ready
[4296898.693000] usbcore: registered new driver sn9c102

```

And lsusb:
```

Bus 007 Device 002: ID 067b:2507 Prolific Technology, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 0c45:6028 Microdia
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

So again, it looks like its there fine. But I don't know where to go from here. I installed camorama, which when I load tells me "could not connect to video device /dev/video0, please check connection." I don't know what else to try, or what I should do to get it working.

Anything? Any advice is better than what I have to go on... I literally don't know the next step to take.

Thanks :)

---

### Post by ranf on 2005-10-24
Try some other apps like `gnomemeeting' or `xawtv'. Not every app works with Video for Linux version 2 (v4l2).

---

### Post by sailor420 on 2005-10-24
OK, gnomemeeting is working just fine. I guess it was just something with camorama.

Anyone know of any other good webcam software? Something that I can use to take pictures, or chat with someone running windows (eyeball chat, yahoo chat, etc compatible)?

---

### Post by idn on 2005-10-25
I have always not bothered to get a webcam because I am unsure of whether I will actually be able to use it, considering all my friends use windows. Has anyone got gaim to use a web cam? If I could chat to friends on msn with a web cam on Gaim I would definately get one :)

---

