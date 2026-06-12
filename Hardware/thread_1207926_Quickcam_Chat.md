---
title: "Quickcam Chat"
date: 2009-07-08
forum: Hardware
---

### Post by Samnsparky on 2009-07-08
Hello! I have a Quickcam Chat (on Intrepid) and I am having some issues. Cheese and Ekiga seem to work but mplayer just displays colored snow with the command mplayer tv:// -tv driver=v4l:width=900:height=600:device=/dev/video0 (and all the variations of width and height that I have tried). I have attempted to use LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so with no luck. I am also trying to get reacTIVision or ccv (tbeta) to work but so far with no avail. reacTIVision just displays snow and ccv just displays black.

Here is the entry from lusb: Bus 002 Device 003: ID 046d:08af Logitech, Inc. QuickCam Easy/Cool

Also this line is displayed a lot by mplayer: ioctl mcapture failed: Invalid argument

Finally, reacTIVision gives me this: 
libdc1394 error: Platform failed to get device list
no DC1394 cameras found
unsupported pixelformat: other
camera: zc3xx
format: 640x480

Any suggestions?

Thanks,
Sam

---

### Post by Samnsparky on 2009-07-11
*bump* sorry...):P

---

### Post by mchiareli on 2009-08-07
Hi, it's working for you?

I can't use the reactivision because of the same problem.... =(

---

### Post by rstets on 2009-10-20
same here.

had a similar issue with ccv-1.2 (ex-tbeta) - it wanted libraw1394.so.8 - but the system had only libraw1394.so.11 - solved but copying and renaming libraw1394.so.11 to libraw1394.so.8...

reactivision wants libdc1394, but doesn't tell which version - system has libdc1394.so.22

---

### Post by rstets on 2009-10-20
I guess I'll try compiling it from source - then I'll know what's missing

---

