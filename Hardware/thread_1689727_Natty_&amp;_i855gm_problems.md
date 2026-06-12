---
title: "Natty &amp; i855gm: problems"
date: 2011-02-17
forum: Hardware
---

### Post by serpetiello on 2011-02-17
Hardware: Fujitsu-Siemens Stylistic ST5022D, featuring an intel i855gm chipset.
 
Ubuntu: 11.04 alpha 2
 
Problems:
- kernel mode setting support is (still) broken for i855gm graphics chipset
- Xv acceleration is not enabled 
 
 
Ubuntu Installation: you have to change the "nomodeset" flag before booting. This means that you can only install Ubuntu using a keyboard. But **before rebooting** at the end of the installation, you need to change the "nomodeset" in the GRUB configuration.
 
I changed the */etc/default/grub *file, uncommenting the line *GRUB_TERMINAL=console* and changing the *GRUB_CMDLINE_LINUX_DEFAULT *to *nosplash i915.modeset=0*
 
But it was not sufficient: at first boot i got a garbage screen (even using an external monitor). Then blindly (yes, blindly) hit CTRL-ALT-F1 to get a text console, then gave user and password, then *sudo bash* and then *update-grub* and then *reboot* and then everything went OK.
 
The *xvinfo* command always says "no adapters present".
 
Note that Ubuntu 8.04 supported Xv very well; then 9.04 had some random freeze during full-screen Xv playback, and later Xv support was completely disabled... up to today.

---

### Post by Anthony25 on 2011-04-06
Hi,
I am running on the natty' beta 1 and your problem is fixed.

But I can't enable Unity because the Accelerated video is off, so I am waiting for a new driver which will fix the problem (maybe the 2.15' version of the package xvideo-xorg-video-intel).

---

### Post by Flotter on 2011-04-19
Did you do a fresh install of Natty beta, or did you upgrade?

I had zip problems with this thing til I upgraded to Meerkat, then my video started giving me fits as in, no adapters present, etc.  I can use mplayer, but I have to use the x11 module with -framedrop.  This is even with a fresh install of Meerkat off the Ubuntu User dvd & a quicckie upgrade to Natty...

---

### Post by Anthony25 on 2011-04-20
I did a fresh install of Natty, and I retry with the beta 2 (fresh install again).

I have found a "solution" : I have modified the xorg.conf file to turn the hardware acceleration on.

But the problem was that compiz was enabled and it wasn't stable, so I made a script to disable compiz on start-up and enable metacity.

The hardware acceleration works perfectly, I have the same performance as on Windows.

Edit : I have some crash, but less than on Maverick.

I will test with the final version, and I hope that it will be fix.

---

