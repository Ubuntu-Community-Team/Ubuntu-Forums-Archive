---
title: "Webcam works for Ekiga but not Cheese"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by dngpng on 2007-09-03
I'm using Feisty, and my webcam, which has the product ID 0ac8:301b, should be supported by the gspca driver.

It works well in Ekiga with the v4l2 driver, however when I open Cheese, nothing is displayed, either in picture mode or video mode.

the dmesg output is normal:
```
[56855.300000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[56855.496000] usb 2-2: configuration #1 chosen from 1 choice
[56855.500000] usb 2-2: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x0AC8/0x301B)
[56855.576000] usb 2-2: PB-0330 image sensor detected
[56855.976000] usb 2-2: Initialization succeeded
[56855.976000] usb 2-2: V4L2 device registered as /dev/video0
```

But when I use the command "gst-launch-0.10 v4l2src ! ffmpegcolorspace ! ximagesink", I got this output:
```
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /pipeline0/v4l2src0: Could not negotiate format
Additional debug info:
gstbasesrc.c(1865): gst_base_src_start (): /pipeline0/v4l2src0:
Check your filtered caps, if any
Setting pipeline to NULL ...
FREEING pipeline ...
```

I also noticed the "could not negotiate format" in the output if I run Cheese in debug mode.

Anyone knows what is the problem? Thanks in advance.

---

### Post by dngpng on 2007-10-31
It's been nearly 2 month and I almost forgot this post.

Just want  to link to another post: [http://ubuntuforums.org/showpost.php?p=3600397&postcount=13](http://ubuntuforums.org/showpost.php?p=3600397&postcount=13) where punong_bisyonaryo have posted a work-around for this problem.

---

