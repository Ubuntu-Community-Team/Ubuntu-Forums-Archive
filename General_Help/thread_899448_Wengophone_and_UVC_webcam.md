---
title: "Wengophone and UVC webcam"
date: 2008-08-24
forum: General Help
---

### Post by juaninse on 2008-08-24
Hi there,

I want to report an issue with Wengophone that I encountered on both Hardy Heron and Gutsy Gibbon.

I am using a Logitech Quickcam Pro 9000, and it works splendidly with the UVC driver... Ekiga and Sky are both able to access the image from the webcam.  However Wengophone is not able to do so.  Wengophone offers many perks which make it my preferred IM/SIP application however, so it MUST run with it too.

It is not a generic fault with Wengo when using webcams however, sinc I am able to run a cheap camera (with the gspca usb webcam driver) without a hitch.  Of course it is NOT  a quickcam Pro... and it shows.

I'm not sure what the problem is.  Both webcams have worked wonderfully as plug and play devices.  Never had to worry about drivers.  They just worked out of the box.  Wengophone seems to have no problems communicating with one of them, and as I imagine it uses V4L to do all communications, if the other programs use V4L to grab the images from the UVC camera, I am at a loss to understand why Wengophone cannot.  If anybody has come accross a similar problem, please let me know if a solution exists.

---

### Post by imon9 on 2008-08-24
it sounded like wngophone is using v4l wherelse the other support v4l2 (uvc is v4l2)

ps: v4l and v4l2 is webcam standards

try install flashcam from ww.swift-tools.net/Flashcam/
it may help

---

### Post by Crafty Kisses on 2008-08-30
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2) if working with the settings does not work or help.
Post the results of the command > lsusb

---

### Post by remjg on 2008-09-07
Hi!

I've the same issue with my UVC webcam "hercules Dualpix Exchange"... It works perfectly on Linux, WengoPhone detects it but I've no image!

If you have an idea... I don't want to use another software because all my friends have a wengo account.

---

