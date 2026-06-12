---
title: "Looking for an inexpensive 1080P WebCam"
date: 2020-03-17
forum: Hardware
---

### Post by PopsTheSailor on 2020-03-17
I'm on 19.10 and I'm looking for an inexpensive external 1080P Webcam. I tried one from Amazon that said it worked with linux. Installed the drivers and still nothing. Looking for something that is plug and play preferably.

---

### Post by TheFu on 2020-03-17
I've using a Logitech C720, but the C710  is reported to work better, but it wasn't shipping when I needed a webcam.

Zoom doesn't work on the C720 that I've found without the proprietary Windows drivers and it is software zoom, not hardware.

Logitech is pretty hostile towards Linux.  Until Google made Chromebooks, many devices didn't work at all with any Linux.  Thanks to google for making those drivers work on Linux.

The microphone built-into the C720 is pretty good compared to others, but it does always take some fiddling with **pavucontrol** to get the input/output stuff correct.

Don't know anything about 19.10. Still using 16.04 here.

[https://smallbusiness.chron.com/zoom-out-webcam-ubuntu-60545.html](https://smallbusiness.chron.com/zoom-out-webcam-ubuntu-60545.html) says VLC can control the zoom, but other Linux webcam apps don't have that ability. IDK.
 
Did some research and testing....to control the zoom, seems this works:
```
$ v4l2-ctl -d /dev/video0 -c zoom_absolute=150
```

Zoom amount for this webcam has to be between 100 and about 170. Higher numbers don't zoom more. Again, this is NOT optical zoom, so the image gets fuzzy.  There are options for panning up, down, left, right, tilt, focus, contrast, brightness .... and lots more. None are optical.
```
$ v4l2-ctl -d /dev/video0 -k --all
```
shows all the available controls.

---

### Post by PopsTheSailor on 2020-03-17
Thanks for the info. Wow, seems like a lot of work. Hopefully someone will have something that is true plug and play. If not, I'll look into those above.

---

### Post by TheFu on 2020-03-17
They are plug-n-play if there aren't any other devices or pulseaudio doesn't decide to do something funky.
No need to hunt down audio or cam drivers. That part just works.

---

