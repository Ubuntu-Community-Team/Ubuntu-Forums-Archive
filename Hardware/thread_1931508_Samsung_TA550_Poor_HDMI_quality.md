---
title: "Samsung TA550 Poor HDMI quality"
date: 2012-02-25
forum: Hardware
---

### Post by Chubbs[] on 2012-02-25
I have a Samsung TA550 connected to a Radeon HD 5770 using fglrx drivers. 

The funny thing is that the picture is fine when using the PC mode, which uses the VGA connection. But if I try to connect using an HDMI cable the image is very distorted. Colors are off and the text appears unfocused. I have provided a picture.

[IMG]http://i39.tinypic.com/rr4h9g.png

Any suggestions on how to fix this? Other than use PC mode. 
I have tried different drivers and playing around in catalyst, it even looks bad when I boot into Windows 7 Installer...

EDIT: That picture doesn't look bad right? Which means that it must be on the monitor side because it still looks grainy. The other funny thing is that an xbox works and looks just fine when connected to this monitor

---

### Post by DirtyPC on 2012-02-25
Hi, This is very common.
It's your refresh rate (hz)
Have a look in ATI Control Center, does it say 24/30hz ? check what hz your monitor should be and change it to that :)

---

### Post by Chubbs[] on 2012-02-25
Thank you! I have changed my refresh rate using xrandr and that got rid of the distortion and such but, I cannot use 1920x1080 resolution. I am forced to use 1280x1024 or something like that.

How can I override xrandr to use 1920x1080 resolution at 75hz?

---

### Post by DirtyPC on 2012-02-26
This is the problem I'm having, haven't found a solution yet,

[http://ubuntuforums.org/showthread.php?t=1931769](http://ubuntuforums.org/showthread.php?t=1931769) watch this thread.

---

