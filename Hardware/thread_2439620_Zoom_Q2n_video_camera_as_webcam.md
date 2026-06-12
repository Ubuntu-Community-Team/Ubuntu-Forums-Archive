---
title: "Zoom Q2n video camera as webcam"
date: 2020-03-30
forum: Hardware
---

### Post by arst06d on 2020-03-30
Hi
I have a Zoom Q2n video camera [https://www.zoom-na.com/products/field-video-recording/video-recording/zoom-q2n-handy-video-recorder#downloads]("https://www.zoom-na.com/products/field-video-recording/video-recording/zoom-q2n-handy-video-recorder#downloads") which I use to record my local music club and post to our Facebook group.
It is supposed to be possible to use this camera as a webcam via USB cable - but my laptop (fully up to date with the latest LTS release) does not recognise the camera.
There are drivers on the Zoom website for both Windows and Mac.

Anyone successfully connected this camera as a webcam, or have any suggestions as to what I can try?

Thanks in advance.

---

### Post by CelticWarrior on 2020-03-30
If you selected the webcam mode according to the instructions on p.18 in your [user's manual]("https://www.zoom-na.com/sites/default/files/products/downloads/pdfs/Q2n_English.pdf") with the USB cable connected and it isn't recognized then it really needs proprietary drivers.

---

### Post by arst06d on 2020-03-30
I was afraid of that!
Thanks.

---

### Post by TheFu on 2020-03-30
Use **lsusb** to get the USB id for the device and start searching the internet for linux drivers for that same chip.  Sometimes, we get lucky.  OTOH, a cheap 720p webcam is about $20, so it won't be the end of the world.  Just be certain to check the current kernels you use for specific built-in webcam support.  For example, my C920 from Logitech "just works" now, after 5 yrs of not working until Google decided that chromebook support for that device was important.  That's my guess.

---

### Post by giosimar on 2020-04-23
> **arst06d said:**
> Hi
I have a Zoom Q2n video camera [https://www.zoom-na.com/products/field-video-recording/video-recording/zoom-q2n-handy-video-recorder#downloads]("https://www.zoom-na.com/products/field-video-recording/video-recording/zoom-q2n-handy-video-recorder#downloads") which I use to record my local music club and post to our Facebook group.
It is supposed to be possible to use this camera as a webcam via USB cable - but my laptop (fully up to date with the latest LTS release) does not recognise the camera.
There are drivers on the Zoom website for both Windows and Mac.

Anyone successfully connected this camera as a webcam, or have any suggestions as to what I can try?

Thanks in advance.

I'm interested in this camera. I'll follow.

---

### Post by arst06d on 2020-04-24
> **TheFu said:**
> Use **lsusb** to get the USB id for the device and start searching the internet for linux drivers for that same chip.  Sometimes, we get lucky.  OTOH, a cheap 720p webcam is about $20, so it won't be the end of the world.  Just be certain to check the current kernels you use for specific built-in webcam support.  For example, my C920 from Logitech "just works" now, after 5 yrs of not working until Google decided that chromebook support for that device was important.  That's my guess.

Running lsusb gives me 

> Bus 001 Device 032: ID 1686:0360 ZOOM Corporation 

I cannot find anything about this.  The Q2n is now discontinued, unfortunately, so no prospect of any updated drivers from the manufacturer.

---

### Post by scott-winslow on 2020-12-05
If you're still interested, I did find a clunky way to make it work.

If you run something like the V4L2 test bench (qv4l2 (previously I used v4l2ucp, but that seems to have been obsoleted)), and in the brief window between selecting "web cam" on the Q2n and it powering itself off you open it in the v4l app, it will stay on as long as you keep it open in the app. At that point it will also show up in other apps like the Zoom.us meeting app (or cheese, etc.). Not an ideal solution, but it works.

Personally I bought the thing to use as a stand-alone camera to video my band, and using it as a webcam is just a "bonus". But I'm definitely disappointed that Zoom, the hardware company, doesn't care about linux....

---

### Post by bcjonesbc on 2021-01-25
I use Q2n with an Acer Chromebook 14 which does not have native support for it. I went to "settings" then "Linux(beta)" . It downloaded and set up a linux container. I did not need to download any additional packages. You do not need to have Linux window open or run any Linux apps to use the Q2n. When I connect the Q2n and start its webcam, I get a pop-up "connect to Linux". The Q2n will turn itself off if you don't quickly click on the popup. Once clicked, the camera is available to both chromebook and linux apps.

---

### Post by Leslie Viljoen on 2021-10-06
I didn't really understand either of those last two replies, but I can report that my Zoom Q2n 4k works in OBS Studio without drivers. OBS Studio can use V4L2, so I suppose that's why.
lsusb says "Bus 001 Device 012: ID 1686:04bc ZOOM Corporation"
OBS version 27.0.1, Ubuntu 18.04.6 LTS.

You need to go to "add source" in OBS and add a "Video capture device (V4L2)".
Both video and auto are working.

Update: 
I installed v4l2ucp and libv4l-0, then was able to use the Camera in Cheese using instructions similar to here:
[https://wiki.gnome.org/Apps/Cheese/FAQ](https://wiki.gnome.org/Apps/Cheese/FAQ)

For my system: > LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libv4l/v4l2convert.so cheese

After this, the camera showed up in Zoom, Skype, Slack and Google Meet.

---

