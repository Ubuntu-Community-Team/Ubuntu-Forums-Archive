---
title: "Inspiron 1520 webcam problem"
date: 2009-12-01
forum: Hardware
---

### Post by nemexs on 2009-12-01
Hey everyone, I currently have a problem with my webcam. 

**********************************
Specifications:
Dell Inpiron 1520
Intel Core 2 Duo T7250 @ 2.00GHz
GeForce 8600M GT 1440x900 pixels
Ubuntu 9.10 Koala
**********************************

There are two cases:

[LIST=1]
[*]1st. The problem with setting up my camera through fire fox
[*]2nd. aMSN webcam doesn't work
[/LIST]

1st. I have tried using my webcam in order to do some bloging, but didn't work, it just stuck with a single image and doesn't continue. 
[IMG]http://img260.imageshack.us/img260/2566/screenshotnx.png[/IMG]

I never faced this problem with cheese and I don't know what to do. I've been facing the same problem with Camorama Webcam Viewer in that case it said this:
[IMG]http://img341.imageshack.us/img341/2070/screenshot1ij.png[/IMG]

I've tried to update the drivers from [here]("http://ubuntuforums.org/showthread.php?t=501195"), but whenever I got to the stage 
[IMG]http://img138.imageshack.us/img138/1173/screenshot2b.png[/IMG]
I just get stuck, since I don't really know how to install it; if anyone could provide me with some tutorial or guidance I would be very thankful. 

2nd. Well the second is connected to the first since my aMSN doesn't work because of the factor that I don't have the drivers installed for it.

If anyone could give me some assistance I would be very thankful :)

Ow P.S. if you do provide the guidance, could you make it the one like, "How to install webcam drivers for complete morons" < Because I'm seriously an idiot in ubuntu.

Thanks 

Have a nice day.

---

### Post by nux_guy22 on 2010-01-25
I have the exact same setup.  I found this on another forum, but I just plugged this in the terminal and the cam came back on 

sudo rmmod uvcvideo
sudo modprobe uvcvideo

Hope it helps

---

### Post by no2498 on 2010-01-26
if his did not help try this
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button
cheese has some good help in it

---

