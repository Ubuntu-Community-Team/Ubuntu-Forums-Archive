---
title: "Webcam Microsoft VX3000, gspca problem"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by amenzix on 2007-11-19
I have a problem with my new VX3000 webcam. I had a quickcam before and it worked perfectly (well, except that the camera itself sucked :P). I read a bit on the net and saw that this camera (045e:00f5) is listed as supported on the gspca site. So I fetched the kmod-gspca from the livna repo (by the way, I'm running Fedora 8, hope that's not a problem). Now, on resolutions lower than 640x480 it looks really crappy, the image is garbled. I don't care that much really, but even on 640x480, the camera shows a weird teal instead of white, and the whole image is pulsating between normal colors and weird yellow. I'm not sure, could this be problem be because of a wrong palette set? Or maybe because v4l doesn't support gain settings, and the camera may have a wrong value?

Thanks in advance!

---

### Post by jespdj on 2007-11-19
You mean something like [this](http://ubuntuforums.org/showthread.php?t=617595)?

---

