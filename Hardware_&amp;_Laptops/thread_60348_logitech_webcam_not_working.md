---
title: "logitech webcam not working"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by gratefulfrog on 2005-08-27
Anyone know where to start to get a logitech quickcam pro 4000 to work?
lsmod shows:
```

$ lsmod | grep pwc
pwc                    82212  1
videodev               12032  2 pwc
$ lsmod | grep video
videodev               12032  2 pwc
video                  18824  0
[/CODE
but running gnomemeeting, I get: 
[CODE]Error while opening video device /dev/video0
```
running xawtv:
```
$ xawtv
This is xawtv-3.94, running on Linux/x86_64 (2.6.10-5-amd64-generic)
WARNING: v4l-conf is compiled without DGA support.
can't open /dev/video0: Device or resource busy
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Device or resource busy
v4l2: open /dev/video0: Device or resource busy
v4l: open /dev/video0: Device or resource busy
no video grabber device available

```
Any help would be appreciated.
Cheers,
GF :roll:

---

### Post by gratefulfrog on 2005-09-12
Here's the solution:

[http://www.ubuntuforums.org/showthread.php?t=24827](http://www.ubuntuforums.org/showthread.php?t=24827)

---

