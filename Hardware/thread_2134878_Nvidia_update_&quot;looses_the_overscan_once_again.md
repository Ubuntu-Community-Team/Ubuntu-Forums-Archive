---
title: "Nvidia update &quot;looses the overscan once again&quot;"
date: 2013-04-12
forum: Hardware
---

### Post by pajopet on 2013-04-12
I run an Nvidia 650 on Linux Deepin using a Panosonic Plazma. The recurring problem with Nvidia driver upgrade is that I loose the overscan controls which are very much needed. I cannot manage to find a copy of the old drivers along with the settings control in order to rectify this blatant quality control issue. I have installed older drivers but the settings panel that should accompany said drivers is without the control. 

Any help would be apppreciated
Thanks in advance

pajo

---

### Post by itlarson on 2013-04-12
I second this issue!  A recent upgrade removed overscan correction from two of my systems.  One has a gt-220 card, and the other is a Zotac Ion- I don't remember the exactexact chipset.

---

### Post by itlarson on 2013-04-12
Excerpt from ask ubuntu:

I finally managed to eliminate overscan on my Panny 32" 720P LCD TV using a combination of "ViewPortIn" and "ViewPortOut" with the beta 302.07 driver.

I played with nvidia-settings commands until I finaly got something that worked:

nvidia-settings --assign CurrentMetaMode="DFP-0: 1920x1080 { ViewPortIn=1920x1080, ViewPortOut=1820x1020+50+30 }"

With that, I added the following line to the "Monitor" section of xorg.conf to make the settings "stick:" Option "MetaModes" "DFP-0: 1920x1080 { ViewPortIn=1920x1080, ViewPortOut=1820x1020+50+30 }"

End of excerpt.

Personaly I have found the first part to work, but haven't found time to edit xorg- although it should work.

---

### Post by pajopet on 2013-04-12
Thank you. I will give that a try
pajo

---

### Post by pajopet on 2013-04-13
Does anyone have
nvidia295.40 64bit ubuntu (Size: 56.74 MB) 

nvidia-current_295.40-0ubuntu1.3_amd64.deb
55.84 MB
*

nvidia-settings_295.33-0ubuntu1_amd64.deb
908.99 KB
*
screen-resolution-extra_0.14ubuntu2_all.deb
12.49 KB

---

### Post by itlarson on 2013-04-13
I have tried the xorg thing, and it works perfectly.  This is the change I made to the "Screen" section of xorg.conf:

old:

Option         "metamodes" "1920x1080 +0+0; 1280x720 +0+0"

new:

Option         "metamodes" "1920x1080 +0+0; 1280x720 { ViewPortIn=1280x720, ViewPortOut=1215x685+31+16 }"

This gives me overscan corection in 1280x720, but not in 1920x1080.  This is perfect for me, since this is for a Mythtv DVR.  It runs in the low resolution so I can read from across the room when using it as a computer, then switches to 1080p when playing back TV recordings.  There's no overscan correction in 1080p, which reduces the load on the GPU, leaving more processing power for deinterlacing.

I'm pretty sure this was all caused by a change in the newest proprietary Nvidia driver.

---

### Post by pajopet on 2013-04-13
So the solution that realy works is yogo to "kickass torrents and search linux then nvidia and the 295.40 64bit drivers +settings can be had.

Don't forget to say thanks. It still accomodates Nvidia series 600

the new unreleased 313.30 drivers should be fine or at least that is their word

pajo

---

