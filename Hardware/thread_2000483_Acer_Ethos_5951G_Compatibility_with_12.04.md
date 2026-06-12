---
title: "Acer Ethos 5951G Compatibility with 12.04"
date: 2012-06-09
forum: Hardware
---

### Post by ehabh on 2012-06-09
I got a new Acer Aspire Ethos 5951G and installed Ubuntu 12.04 on it here is what works.

Right after the install

Wifi works
Bluetooth works
Trackpad works this is suprising taking into account that the trackpad is very non standard and is removable and usable as a remote. The trackpad sometimmes misbehaves but the same thing happens in windows.
Out of the box graphics most probably Intel graphics is the one that is the default.
Bumblebee works but as far as I can see I do not know how to get a list of which is working and which is not. But it seems that both work  as per commands below

glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
303 frames in 5.0 seconds = 60.503 FPS
301 frames in 5.0 seconds = 60.175 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1500 requests (1500 known processed) with 0 events remaining.
ehab@ehab-Aspire-5951G:~$ optirun glxgears 
3607 frames in 5.0 seconds = 721.249 FPS
3750 frames in 5.0 seconds = 749.936 FPS
3923 frames in 5.0 seconds = 784.453 FPS
[VGL] ERROR: in readback--
[VGL]    244: Window has been deleted by window manager


See with optirun the speed is 10 times or more!

Sound works without an issue.


So overall no real headaches, battery seems a bit fast to drain but I did not really try it in windows to compare.


[my blog]("http://ehab.blog.mashy.com")

---

### Post by ehabh on 2012-11-25
With recent updates I am starting to get random forced restarts with no warning on this machine.

---

