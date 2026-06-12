---
title: "Cant get 1366x768 with Ubuntu on Acer 751h"
date: 2009-06-18
forum: Hardware
---

### Post by brainchill on 2009-06-18
Does anyone have one of these netbooks that they are getting the full resolution in ubuntu 9.0.4 (or any other distro for that matter)? What am I missing here. The best I can get is 1024x560

---

### Post by kevdog on 2009-06-29
did you ever get this figured out?

---

### Post by brainchill on 2009-07-04
Create 

/etc/apt/sources.list.d/ubuntu-mobile.list 

with this in it

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

Then,

gpg --keyserver keyserver.ubuntu.com --recv 0c713da6
gpg --export --armor 0c713da6 | sudo apt-key add -

apt-get update
apt-get install xserver-xorg-video-psb

Then reboot and everything just works!

---

### Post by pento on 2009-08-02
Hmm, it seems that this workaround doesn't work in 2.6.28-14 kernel.

> dpkg -l | grep psb
ii  libgl1-mesa-dri-psb                        0.25-0ubuntu1~810um1.1                    Implementation of the OpenGL API -- for Poulsbo (psb)
ii  poulsbo-driver-2d                          1.1-0ubuntu1~904um1                       Metapackage for the 2D Poulsbo (psb) X11 driver.
ii  psb-modules                                4.41.1-0ubuntu1~904um1                    Kernel module built for -generic or -lpia kernel
ii  xserver-xorg-video-psb                     0.31.0-0ubuntu1~904um1                    X.Org X server -- Intel Poulsbo (2D)



From Xorg.0.log

> (II) PSB(0): Debug: psbScreenInit
(II) PSB(0): Debug: psbDRIScreenInit
(II) PSB(0): Debug: SAREA size is 8192
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "psb"
(EE) [drm] drmOpen failed.
(EE) PSB(0): [dri] DRIScreenInit failed. Disabling DRI.
(EE) [drm] Could not uninstall irq handler.
(EE) PSB(0): This driver currently needs DRM to operate.

Fatal server error:
AddScreen/ScreenInit failed for driver 0

---

### Post by AmyRose on 2009-08-25
You also need this:

sudo apt-get install poulsbo-driver-3d psb-kernel-source

Worked for me on my Mini 12.

---

