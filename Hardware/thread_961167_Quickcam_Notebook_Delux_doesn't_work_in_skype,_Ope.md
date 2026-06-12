---
title: "Quickcam Notebook Delux doesn't work in skype, OpenCV"
date: 2008-10-28
forum: Hardware
---

### Post by SuperSack56 on 2008-10-28
I'm trying to do various things with my Logitech QuickCam Notebook Delux. It seems like some applications are able to use it, and some completely choke. Most important is getting OpenCV working, which currently times out after several minutes of trying to initialize the camera (in some of their sample programs).

lsusb output:
Bus 005 Device 002: ID 046d:08d8 Logitech, Inc. QuickCam for Notebook Deluxe

In Skype, trying to preview the video in the Options screen either segfaults and quits, or displays a weird green snowy image.

Cheese works fine.

running gstreamer-properties and 'test'ing the video (selecting V4l2 and the USB camera) works fine.

VLC seems to be unable to open it as a Capture Device - it shows a little webcam application picture, and sits forever.

v4l-conf gives the following:
matt@silk:~$ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1280x800, depth=24, bpp=32, bpl=5120, base=unknown
/dev/video0 [v4l2]: no overlay support

It seems weird to me that there's no overlay support. Any thoughts as to how to get this working is appreciated; as usual, let me know if i can post anything additional...

---

### Post by gabitogol on 2009-03-08
Hi,

Just say I´m having the exact same problem, but with different camera.

lsusb

Bus 002 Device 003: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX

Right now the mayority of the applications are porting their code to use the new version of the drivers libv4l.
You can find the solution for OpenCV here:

[http://sourceforge.net/tracker/index.php?func=detail&aid=2653321&group_id=22870&atid=376677](http://sourceforge.net/tracker/index.php?func=detail&aid=2653321&group_id=22870&atid=376677)

---

### Post by 188236 on 2010-02-06
I have the same deviceID ( 046d:08d8 ) like SuperSack56 an exactly the same problem. Cheese works, skype doesn't. 
I tried a lot of thinks but now I have no hope anymore. Its simply not compatible (but it once was! In Version 8.10 it worked!). 

Any suggestions?

---

### Post by 188236 on 2010-04-11
After many tries I finally found the solution. Its NOT a problem of ubuntu but a bad configuration of skype. Here you can read how to fix it:
[http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html]("http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html")

---

