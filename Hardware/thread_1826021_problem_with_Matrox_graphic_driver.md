---
title: "problem with Matrox graphic driver"
date: 2011-08-16
forum: Hardware
---

### Post by baumtopf on 2011-08-16
Hello Ubuntu users,

I get the problem, that I cannot play movies for example with AVI format.
At the first time, where I played a movie, it works. But it appears an error message. 
This error message says that my video speeding up doesn't support 1920x1080 Pixel.
It supports only a maximal resolution of 1024x1024 Pixel. 
I take a screenshot of this error message and I attached it in this post.
But it is in German. I take also a screenshots of all packages which I installed, for example gstreamer. It supports mpeg, divx, mpeg4, ac3, wmv, asf, mp3, sid, mpeg1, mpeg2, ac-3, DVD, MMS, Wavpack, Quicktime, Musepack, AAC, XVID, Mpeg2, FAAD. I tried also play movies with vlc and totem. But it also doesn't work. My Additional Drivers says "No proprietary drivers are in use on this system" and it doesn't find a driver which I can install.

Information about my graphics card and graphic driver:
01:00.0 VGA compatible controller [0300]: Matrox Graphics, Inc. MGA G400/G450 [102b:0525] (rev 85)
    Subsystem: Matrox Graphics, Inc. Millennium G450 DVI [102b:23c3]
    Kernel driver in use: matrox_w1
    Kernel modules: matrox_w1, matroxfb_base

What can I do now?
Look at my attachments. Maybe someone get a good idea.

Regards, baumtopf

---

### Post by realzippy on 2011-08-16
That matrox hardware is pretty old (EOL),there is no matrox driver to install.
The matrox kernel module already is activated.
Maybe your device has not enough videoram for this resolution?
You could try to lower color depth to 16bit...but suggest some googling first.

---

