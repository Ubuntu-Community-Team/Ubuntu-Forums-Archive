---
title: "agp graphics card"
date: 2010-06-24
forum: Hardware
---

### Post by jupitertsax on 2010-06-24
i recently installed 2 new pices of hardware.
first i installed 1GB of ram which works fine but i had had trouble with it in the past with ubuntu.
second was a visiontek ati radeon graphics card.

i am able to get into the standalone terminal but when i try to start the x server of start gdm they come up with a bunch of error messages ( i will copy and post the if they are needed). i do not have a third party driver for it because i have only been into the live cd (which works fine)

---

### Post by VH-BIL on 2010-06-24
First try and switch the driver to vesa. You can do this by editing the xorg.conf file with:
```
sudo nano /etc/X11/xorg.conf
```
If you do not have this file you can create one by:
```
sudo Xorg -configure
```

---

### Post by efflandt on 2010-06-24
Have you tested the memory with memtest86+ from the grub menu?

What video chip does your card have?  I have an older Visiontek AGP ATI X1300 and I had to use **nomodeset** (or **radeon.modeset=0**) kernel boot parameter to fix general video sluggishness and failure to for video to turn off for suspend or hibernate.  Although, my desktop still booted fine with the default kms (kernel mode setting driver) other than those issues.  But I had to also use those parameters on a laptop with ATI Mobility X1300 to avoid boot graphics glitch and hang.  Other than that I am using default modules.

I tried using radeonHD on the desktop, but that did not automatically find the native resolution of my DVI to HDMI connected HDTV (used as monitor) and seemed to also need other configuration that was more trouble than it was worth (glxinfo threw an error recommending setting vblank_mode and glxgears locked up the computer).

---

