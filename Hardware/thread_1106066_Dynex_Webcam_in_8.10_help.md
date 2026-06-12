---
title: "Dynex Webcam in 8.10 help"
date: 2009-03-25
forum: Hardware
---

### Post by ckgreenman on 2009-03-25
Hello, I'm having a heck of a time getting my Dynex webcam to work under Intrepid.  I vaguely remember getting it working under Hardy but I don't remember what I did.  

The webcam is recognized, the drivers are loaded and the /dev/video0 device is created.  I also found I had to set LD_PRELOAD to point to the v4l1compat.so library.  The problem I'm running into is when you try to actually use the camera.   I've tried Camorama, Camstream, Cheese, and luvcview and either they can't open the video stream or they display a dark distorted picture.  I had a similar problem in 8.04 with certain resolutions but in 8.10 it does it in all resolutions and I can't get a decent picture.

Any suggestions?

---

### Post by teaker1s on 2009-03-25
you can play around with settings and when happy configure them permanently.

It's not for your cam but I wrote a howto for mine-maybey the colour correction will help

[https://help.ubuntu.com/community/046d%3A08af%20Logitech%2C%20Inc.%20QuickCam%20Easy/Cool]("https://help.ubuntu.com/community/046d%3A08af%20Logitech%2C%20Inc.%20QuickCam%20Easy/Cool")

---

### Post by ckgreenman on 2009-03-30
Thanks for the link unfortunately it doesn't seem to apply to Intrepid.  I was unable to find those settings since the gspca drivers seems to have been split up.  I have 2 modules loading, gspca_main and gspca_sonixj.  I looked in both and the _main location did have a paramters directory but the files mentioned do not exist.  I also tried starting up gqcam and am able to tweak the colors settings but they don't appear to do much of anything.

This is what I'm seeing.

[IMG]http://i257.photobucket.com/albums/hh215/ckgreenman/Webcam-1237915933.png[/IMG]

---

### Post by teaker1s on 2009-03-30
I'm not sure what to suggest except, have you considered contacting the developers-they may be able to further Identify your cam image issue

---

