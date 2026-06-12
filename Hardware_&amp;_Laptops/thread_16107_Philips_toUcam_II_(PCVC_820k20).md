---
title: "Philips toUcam II (PCVC 820k/20)"
date: 2005-02-19
forum: Hardware &amp; Laptops
---

### Post by Gmini on 2005-02-19
Hello,

I would like to install my webcam.

I can read that when I make dmesg :

usb 1-2: new full speed USB device using address 5
drivers/usb/media/ov511.c: USB OV518 video device found
drivers/usb/media/ov511.c: Device revision 1
drivers/usb/media/ov511.c: Compression required with OV518...enabling
drivers/usb/media/ov511.c: Sensor is an OV6630AF
drivers/usb/media/ov511.c: Device at usb-0000:00:02.0-2 registered to minor 0
drivers/usb/media/ov511.c: No decompressor available

Could you help me please ?  :-?

---

### Post by john_walsh54 on 2005-06-15
I could only get my Philips Toucam Pro webcam (PCVC740K) on Ubuntu 5.04 to work when I installed libpt-plugins-v4l. I re-ran the configuration druid in GnomeMeeting and on the Video page, there were two options; v4l and v4l2. When I selected v4l, I was prompted to select "740" which configured the driver for the webcam.
I was pretty confident it would work because before the install, I ran the following commands in Terminal;
john@ThinkPad:~$ gst-launch-0.8 v4lsrc ! xvimagesink
RUNNING pipeline ...
john@ThinkPad:~$ gst-launch-0.8 v4l2src ! xvimagesink
RUNNING pipeline ...
ERROR: from element /pipeline0/v4l2src0: Could not get/set settings from/on resource.
Additional debug info:
v4l2_calls.c(60): gst_v4l2_get_capabilities: /pipeline0/v4l2src0:
Error getting /dev/video0 capabilities: Invalid argument
ERROR: pipeline doesn't want to play.
For the first gst command (gst-launch-0.8 v4lsrc ! xvimagesink) a window appeared with the webcam running. The second gst command seems to had an error similar to GnomeMeeting i.e. it cannot find /dev/video0

---

