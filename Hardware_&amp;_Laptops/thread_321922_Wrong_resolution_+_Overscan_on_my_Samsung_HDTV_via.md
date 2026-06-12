---
title: "Wrong resolution + Overscan on my Samsung HDTV via nVidia"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by Shiva_T on 2006-12-19
Hi,

I'm running Ubuntu Edgy, and have installed the NVIDIA proprietary drivers. However, they evidently aren't very functional, as the highest resolution option it gives me is 1280x720. I'm using a 1080p Samsung HDTV via DVI-HDMI, and it overscans quite a bit. So I have two problems:

1. I can't set the resolution higher than 1280x720.
2. At 1280x720 or even 800x600, the TV is overscanning like crazy.

What I'd really like to do is to set the resolution to 1840x1036, which works perfectly in Windows and gives me a full, non-overscanned desktop.

Any ideas how to do this?

Thanks!

---

### Post by fearevilleet on 2006-12-24
I am having the exact same issue. Under windoze I used a program called powerstrip which would let me set custom resolutions very easily. I can not figure out how to configure ubuntu to a custom tv resolution. If you have found a way please let me know.

---

### Post by kotter71 on 2007-08-09
Why doesn't anybody know this answer?  The best response I've had so far is to install Windows XP, install PowerStrip, figure the modeline, copy and paste to a text file, print out text file, install Ubuntu, and so on...

Seriously, is this the only alternative?

---

### Post by fearevilleet on 2007-08-09
Ya I am not going through all that. It works it is just a pain to see things from far away. At least i can make the text bigger in firefox

---

### Post by lonce on 2007-08-27
I think your problem is the EDID.  When you hook up the TV it sends data to the video card telling it what it can handle.  Sometimes its read wrong, resulting in the issue you are having.

If you go into your xorg.conf and turn off the edid then you should be ok.

---

