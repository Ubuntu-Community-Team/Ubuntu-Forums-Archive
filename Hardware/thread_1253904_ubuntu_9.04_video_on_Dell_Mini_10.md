---
title: "ubuntu 9.04 video on Dell Mini 10"
date: 2009-08-30
forum: Hardware
---

### Post by Lisanels on 2009-08-30
I got my video working.  Here are the packages I had to install.  I'm now running with 1366x768 and video is much better.  I can watch movies on this thing now.  Before I found these packages, it was really choppy.

root@samantha-laptop:~# dpkg -l | grep psb
ii  psb-firmware                               0.30-0ubuntu1~904um1                      Binary firmware for the Poulsbo (psb) 3D X11
ii  psb-kernel-source                          4.41.1-0ubuntu1~904um1                    Kernel module for the Poulsbo (psb) 2D X11 d
ii  psb-modules                                4.41.1-0ubuntu1~904um1                    Kernel module built for -generic or -lpia ke
ii  xpsb-glx                                   0.18-0ubuntu1~904um1                      X11 drivers for Poulsbo (psb) 3D acceleratio
ii  xserver-xorg-video-psb                     0.31.0-0ubuntu1~904um1                    X.Org X server -- Intel Poulsbo (2D)
root@samantha-laptop:~# 

Hope this helps.
Lisa

---

