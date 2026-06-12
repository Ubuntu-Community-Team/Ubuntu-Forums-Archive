---
title: "VGA adapter for Fujitsu U2010/U820"
date: 2009-03-05
forum: Hardware
---

### Post by xingmu on 2009-03-05
I am need to get VGA output working for a Fujitsu UMPC (U2010/U820).  The handheld comes with RJ45/VGA adapter (product no. FPCCBL26).  It plugs into a port in the front.

I am running the VESA driver since the graphics card (Intel GMA 500) is not supported yet.  The display settings dialog does not show any external monitors, nor does the hotkey for switching to VGA output work.  I tried to run xrandr -q and there is no VGA device listed, only the built-in LCD.  I am wondering if the VGA adapter is even recognized?  When I unplugged it and plugged it back in, I saw nothing in the dmesg output.  How can I find out more information on this adapter and its support status in Ubuntu 8.10?

---

### Post by Anfanglir on 2009-06-05
Hi,
a late reply. There is some support for external display through the adapter if you install the GMA500 drivers from these repos:

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

Add ppa key as described in link from this page:
[https://launchpad.net/~ubuntu-mobile..._filter=jaunty](https://launchpad.net/~ubuntu-mobile..._filter=jaunty)

Install libdrm-poulsbo1 and xserver-xorg-video-psb through synaptic. Reboot.

The resolution for the external display is limited to the one setting (1280x800) used by internal display. When I tried it on an old spare 15" screen (non widescreen) the display was slightly distorted. Might look better on a wide screen.

/ Anfanglir

---

