---
title: "Webcam doesn't work on eee pc 1005ha"
date: 2010-01-12
forum: Hardware
---

### Post by alejandro5042 on 2010-01-12
I can't seem to get the webcam to work on Cheese or on Skype with the UNR 9.10 on my 1005ha. I have searched high and low and I cannot seem to find anybody else with this issue.

How can I help you help me? What should I run for you guys? I'm computer savvy, just not on Linux (yet).

---

### Post by alejandro5042 on 2010-01-12
I ran gstreamer-properties and got the following:
```
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(482): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src3:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline1/GstV4lSrc:v4lsrc2]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(482): gst_v4l2_open (): /GstPipeline:pipeline4/GstV4l2Src:v4l2src5:

```
Running lsusb I do not get anything that resembles a video camera... just Linux Foundation root hubs.

I guess Ubuntu doesn't know my camera is there?

---

