---
title: "The Solution to most of the Display Issues!"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by Triton on 2005-07-11
I'm pretty sure that I found the answer to many of the display issues with the i810 video and or flat panel resolution.  Not sure why this works but here it goes...

This will work for GDM and well as KDM!

I added or changed the following in my /etc/X11/xorg.conf

In your Section "Device" add the following

Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Device"
        Driver          "i810"
        > Option  "VideoRam"      "7892k"
        BusID           "PCI:0:2:0"
        > Screen          0 
EndSections

and then make your Section "Monitor" look like this

> Section "Monitor"
        Identifier      "hp L1730"
        HorizSync       30-83
        Option  "DPMS"
EndSection


Actually I think that probably omitting the VertRefresh did the trick!

I hope this works for you all because I spent months trying to get my config to work correctly!   :mad: 

I also was sick of Ctrl-Alt-F2 and then Alt-F7.

2 THINGS OF NOTE!!!

BE SURE TO BACK UP YOUR XORG.CONG

AND

IF YOU HAVE DIFFERENT HARDWARE MAKE SURE YOU RESEARCH THE PROPER PARAMETERS!

I WILL NOT BE MADE RESPONSABLE IF SOMETHING GOES WRONG!


Good luck

Triton

---

### Post by Triton on 2005-07-13
Has anyone had any luck with this?

---

### Post by baaaan on 2005-07-18
What issues will this supposedly resolve? My issue is that I can't get any video modes higher than 640x480 on a brand new system running 82865G video adapter and a 17" (brand new) monitor.

Brandon

---

### Post by sneax on 2005-08-21
I think what the topic starter said might help you Brandon. You could try!

---

### Post by barratt_sab on 2005-09-30
Triton - you are a god.  I have been fiddling with this for about 24 hours straight now, and with the adjustments set out above and fixing up the BIOS setting for display memory my gorgeous 17" tft finally looks like it's worth the money I paid for it.

Thanks


Stephen  :D

---

