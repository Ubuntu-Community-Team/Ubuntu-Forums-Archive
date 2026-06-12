---
title: "Logitech Webcam stopped working"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by cwoehrmann on 2007-11-01
Hi!

Few days ago I installed ubuntu 7.10 and my Logitech Quickcam Notebook worked pretty fine in aMSN, with Flash (Tokbox.com) and Ekiga. Now all of a sudden it stopped working. When the Flash Player tries to acess it, Firefox crashes. aMSN just gets a black picture although it detects a camera. In Ekiga I suddenly got a message that dev/video0 could not be accessed. I played around with it and saw that it had v4l in the video settings page. I changed it to v4l2 and sudddenly I got a perfect picture. But for Flash and aMSN I still have the same errors. I also tried installing the SPCA5xx but it didnt help. 

My /dev/video0 is there. Here my dmesg:

[ 6516.648000] usb 1-2: new full speed USB device using uhci_hcd and address 9
[ 6516.852000] usb 1-2: configuration #1 chosen from 1 choice
[ 6516.852000] usb 1-2: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x046D:0x08AE)
[ 6516.896000] usb 1-2: PAS202BCB image sensor detected
[ 6517.256000] usb 1-2: Initialization succeeded
[ 6517.256000] usb 1-2: V4L2 device registered as /dev/video0
[ 6636.844000] usb 1-2: Device /dev/video0 is busy...
[ 6637.348000] usb 1-2: Device /dev/video0 is busy...
[ 6637.668000] usb 1-2: Device /dev/video0 is busy...

Any help is appreciated. Thanks a lot

---

### Post by Mustard on 2008-02-29
I'm not sure which drivers your cam is using, but if it is using the uvc drivers then this might be relevant...

My take on the situation is that the uvc drivers are only using v4l2, so v4l1 apps are no longer going to funciton with cams using uvc drivers.  Also the latest flash doesnt support v4l2 either.  There is no word from Adobe about when v4l2 is going to become implemented in Flash.

---

