---
title: "webcam Trust"
date: 2019-03-08
forum: Hardware
---

### Post by bananaoverlord on 2019-03-08
Hello guys :D
Im quite new ubuntu user, so please dont get angry xD
Im trying to use my webcam (for coding) but when I start cheese it tells me that No device was found.
Computer looks like its there....
please help :icon_frown:

[ATTACH=CONFIG]282720[/ATTACH]

---

### Post by TheFu on 2019-03-08
First, please copy/paste text. Images waste bandwidth and some people pay for each byte here.

As a new user, it really isn't an ubuntu specific question, learning to think multi-user is one of the hardest things.  The permissions on the video0 device would necessitate that a normal userid be in the "video" group to have access. You can check that using the **id** command.  The fact that there is a video0 device means that the driver for it was loaded and will most likely work fine.  It is likely this is a permissions issue, nothing more.

File and directory permissions are core to all Unix security and learning them ASAP will save you hours, days, weeks, months, and perhaps years of frustration.  Plus, this knowledge is useful for every OS you use, except 1.  All the other OSes are based on Unix, like Linux, and Ubuntu.
A good, free, no-hassle, book to learn the fundamentals in the correct order: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

I haven't tried to use cheese in a long time. It was a few years ago and I didn't get it working for the needs I had at the time. I ended up using something else. Sorry, I don't remember the exact solution, but for video production I use OBS these days. It is overkill if you just want to record a talking head, but if you want to record multiple video sources, desktops, and multiple audio sources, OBS is the best of the non-proprietary option that I know.

Welcome to the forums.  Don't know if any of this is helpful

---

### Post by him610 on 2019-03-09
Hey bananoverload,

You are missing something, the line that ends in *media0*, this is what the output should look like....
```

$ ls -la /dev/ | grep video
crw-rw----   1 root video    29,   0 Mar  9 05:29 fb0
crw-rw----   1 root video   236,   0 Mar  9 07:14 media0
crw-rw----+  1 root video    81,   0 Mar  9 07:14 video0

$ lsusb | grep -i webcam
Bus 001 Device 007: ID 046d:0807 Logitech, Inc. Webcam B500

```

---

