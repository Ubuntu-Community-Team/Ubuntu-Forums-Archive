---
title: "logitech webcam worked in jaunty - does not in karmic"
date: 2009-12-29
forum: Hardware
---

### Post by zablalbaz on 2009-12-29
Hey All,

I have a USB logitech webcam that worked out of the box with Jaunty (cheese and skype both).  I reloaded the same system with Karmic, and I can no longer get the camera to work.  Testing with Cheese brings up a blank screen - no picture at all.  Anyone know if any new bugs were introduced with Karmic that could cause this issue?


lsusb output:
Bus 002 Device 005: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500

Kernel:
2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Cheese error message:
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits

Thanks!

---

### Post by Silvernail on 2010-01-01
My version is:
> dave@dave:~$ dmesg | grep ubuntu
[    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
dave@dave:~$ 

> dave@dave:~$ lsmod | grep video
uvcvideo               59080  0 
videodev               36736  2 vloopback,uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
video                  19380  1 i915
output                  2780  1 video
dave@dave:~$ 

My camera is a different modle.
> Bus 001 Device 004: ID 046d:09a2 Logitech, Inc. QuickCam Communicate Deluxe/S7500


For me, the following applications either put a video on my screen or a snap shot on my HD.

kamoso
cheese
camE
XawTV
luvcview
uvccapture
vlc

Try one of these to see if the error is consistent across apps.
If needed, your capture device is /dev/video0.

---

### Post by Silvernail on 2010-01-01
Let me add to the above post.

Applications > Sound & Video > Webcamstudio > About > go to [http://www.ws4gl.org](http://www.ws4gl.org) [COLOR="Red"]and followed directions to always allow ustream.tv to access my Logitech 9000 web camera [/COLOR] from my browser.

I now  have a 'ustream' image on my screen.

---

