---
title: "Can't use 2 Easycap DC60 devices at the same time"
date: 2012-10-10
forum: Hardware
---

### Post by Skerit on 2012-10-10
I'm setting up ZoneMinder right now, but I'm running into an important issue: I can only capture 1 device at a time.

Not only in zoneminder, system wide.

If I plug in 2 Easycap devices I can watch one but not the other.

Zoneminder's debug isn't very helpful I'm afraid:

```

'zmc -d /dev/video1' exited abnormally, exit status 255
Failed to capture image from monitor 3 (0/1)
Capture failure, possible signal loss?: Input/output error
socket_sendto( /tmp/zm/zms-217602s.sock ) failed: No such file or directory
Starting Capture
'zmc -d /dev/video1' started at 12/10/10 09:34:26
'zmc -d /dev/video1' starting at 12/10/10 09:34:26, pid = 4279
Starting pending process, zmc -d /dev/video1

```

At first I thought: the usb isn't providing enough power. So now I'm using a dc powered usb hub. But still no go.

I can try guvcview with the capture device that is already working, then I get:

```
vid:ffffffff 
pid:4000063 
driver:easycap
checking format: 1498831189
Unable to set 1/25 fps
VIDIOC_S_PARM error: Ongeldig argument
fps is set to 1/25
drawing controls

NEXT_CTRL flag not supported
fps is set to 1/25
Checking video mode 360x288@32bpp : OK 

```

When I then try it with the other device I get an v4l2 init failure.
Well, if it wants to start at all, that is:

```
vid:0000 
pid:0000 
driver:easycap
checking format: 1196444237
Format unavailable: 1196444237.
Init v4L2 failed !! 
Init video returned -2
trying minimum setup ...
video device: /dev/video1 
ERROR opening V4L2 interface for /dev/video0
Unable to find parent usb device.Init. EasyCAP DC60 (location: usb-0000:00:1d.7-5.1)

```

---

### Post by Skerit on 2012-10-11
It was a weird motherboard and power related problem. (Even with a powered usb hub I could only get 1 cam running)

I kept the ubuntu install but replaced the entire computer, now everything is running smoothly.

---

### Post by evildeejay on 2012-12-26
I've the same problem with a netbook. Could you give me more information about your PC where you can use 2 easycap at the same time?

---

