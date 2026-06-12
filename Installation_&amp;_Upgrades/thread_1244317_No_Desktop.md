---
title: "No Desktop"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by grandpaken on 2009-08-19
I've been trying to get a working Myth box going for about 2 months now and have, for numerous reasons failed.  Most have to do with my ATI x1600pro video card connected via
component cables.  I had Jaunty basically setup last week by downgrading the Jaunty xserver to  the intrepid version then loading the older ATI drivers that support my card.  That allowed me to set my desktop to resolutions  higher than 800x600  but all video (even DVD rips) was jerky because I couldn't get 3D support working. I decided to try the radeonHD driver but kept getting a LowRes message caused by the failure to find any modes.  After 10-20 attempts at getting it working I did something that destroyed the install.   

  After a little more research I did a fresh install of Jaunty today, ran update manger then rebooted.   All looked fine with Myth loading so I exited myth to install the radeonHD drivers but all I get is a blank screen with a working mouse.  Right clicking does not bring up the menu.  I can do ctl-alt-f2-3 etc to load a terminal window but that's about it.  The only thing I did different with this install was during the update I told it to use a  new Samba smb.conf file.        

  So ..how do I get my desktop back.

  Even though I might sound like I know what I'm doing I know nothing.

---

### Post by dstew on 2009-08-19
Try booting in Recovery Mode and doing xfix.

---

### Post by grandpaken on 2009-08-21
> **dstew said:**
> Try booting in Recovery Mode and doing xfix.

Thanks but that didn't fix the problem.  I also tried the repair package function.  I did, however, get
a working desktop by editing my xorg.conf file and changing vesa to radeonhd.  I then got a message that
it was using low graphics mode and after a couple screens myth loaded.  Exiting Myth now shows a working desktop.  Now...anyone have settings for xorg.conf using ATI x1600 radeonhd driver over component video to a CRT RPTV that supports 480i, 480p and 1080i?   Is there some kid of setup program for radeonhd that enters the proper settings in the xorg file?

---

