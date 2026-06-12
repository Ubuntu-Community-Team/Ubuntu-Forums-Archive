---
title: "Quickcam Zoom for Skype on 64 bit Jaunty"
date: 2009-06-09
forum: Hardware
---

### Post by geokker on 2009-06-09
I've poked about the web but have just been confused and frustrated. For my sins, I have Xubuntu Jaunty running on an AMD 64 bit box with Skype 2.0 running. Everything works fine except for video - the usual suspect.

I want to get video/audio working with Skype using a Logitech Quickcam Zoom (the one with a built-in mic).

I've installed the V4l libraries and tried the

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

trick to no avail. According to 'lsmod | grep videodev' I need a PWC driver:

```
~$ lsmod | grep videodev
videodev               45184  2 pwc,compat_ioctl32
v4l1_compat            23940  1 videodev
```

Is there anything else I can try?

The camera doesn't work with Cheese either.

---

