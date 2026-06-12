---
title: "Help with genius webcam"
date: 2013-12-13
forum: Hardware
---

### Post by hg088 on 2013-12-13
Hi, I'm trying to get my Islim 300X genius camera to work.

lsusb:
```
Bus 003 Device 002: ID 093a:262c Pixart Imaging, Inc.
```

There are no linux drivers on the genius website.

I've run "kamoso" but it doesn't recognize the camera at all.

How should i proceed?

---

### Post by hg088 on 2013-12-13
Also, i saw this in the syslog when plugin the camera:

```
[    6.964539] usbcore: registered new interface driver gspca_pac7302
```

What can i do with this?

---

### Post by coldraven on 2013-12-14
I'm not sure if this will work in Kubuntu but it has solved problems in Ubuntu.
It seems that some cameras are actually working but just show a very dark picture.
To fix this install "uvcview" and uncheck any "Autolevels", then adjust the Brightness control.
Then quit uvcview, there is no need to save. Then try your camera in whatever program you are using

---

### Post by hg088 on 2013-12-14
> **coldraven said:**
> I'm not sure if this will work in Kubuntu but it has solved problems in Ubuntu.
It seems that some cameras are actually working but just show a very dark picture.
To fix this install "uvcview" and uncheck any "Autolevels", then adjust the Brightness control.
Then quit uvcview, there is no need to save. Then try your camera in whatever program you are using
Thanks I'll try that out

---

### Post by hg088 on 2013-12-14
Looks like the problem was that i had the cam plugged into a usb 3.0 port, because i moved it to a 2.0 port and it worked right away. I find this weird because i though you could plug 2.0 devices in 3.0 ports.
Also, if anyone is having the skype black screen problem like i did try this [http://ubuntuforums.org/showthread.php?t=1997828](http://ubuntuforums.org/showthread.php?t=1997828)

---

