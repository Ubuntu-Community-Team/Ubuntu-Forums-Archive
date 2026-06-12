---
title: "Help: Webcam will not work for GnomeMeeting, but works for gst"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by john_walsh54 on 2005-06-10
I ran the GnomeMeeting wizard to configure my Philips TouCam Pro (PCVC740K) but it failed on the video test. I ran the following commands in Terminal as suggested by a post:
john@ThinkPad:~$ gst-launch-0.8 v4lsrc ! xvimagesink
RUNNING pipeline ...
john@ThinkPad:~$ gst-launch-0.8 v4l2src ! xvimagesink
RUNNING pipeline ...
ERROR: from element /pipeline0/v4l2src0: Could not get/set settings from/on resource.
Additional debug info:
v4l2_calls.c(60): gst_v4l2_get_capabilities: /pipeline0/v4l2src0:
Error getting /dev/video0 capabilities: Invalid argument
ERROR: pipeline doesn't want to play.
For the first gst command (gst-launch-0.8 v4lsrc ! xvimagesink) a window appeared with the webcam running. The second gst command seems to have a error similar to Gnomemeeting i.e. it cannot find /dev/video0
Does anybody know how I configure GnomeMeeting to work like gst?
I am not familar with gst but is it possible to use it like GnomeMeeting? if so, How do I configure it as the window that appeared didn't seem to have any configuration options?

Kind Regards 
John

---

### Post by john_walsh54 on 2005-06-16
I could only get my Philips Toucam Pro webcam (PCVC740K) on Ubuntu 5.04 to work when I installed libpt-plugins-v4l. I re-ran the configuration druid in GnomeMeeting and on the Video page, there were two options; v4l and v4l2. When I selected v4l, I was prompted to select "740" which configured the video for the webcam.

---

