---
title: "VESA will output 1024x768 but not 800x600 or lower."
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by vintagevalves on 2007-07-30
Sounds funny, but I really want to run this machine at 800x600!
It's a Sager (Clevo / Alienware) 5600P notebook.  Has ATI Radeon 7500 M7 mobility graphics and a Samsung LTN150P2-L01 15.1" 1400x1080 display.  

I can run the monitor at any resolution from 640x480 all the way up to 1400x1080 using the "ati" driver in my xorg.conf.  However the 'ati' driver does not play nice with 'atitvout.'  I'd like to be able to use the S-video out to drive my TV with mythtv.  I tried about 4 different builds of the GATOS modified ATI driver, but can't get their TV-out to work - I think it's a Feisty compatibility issue.  It appears that the driver was re-licensed and development may now continue - but for now it doesn't seem to work for me.  

The VESA driver boots 1024x768 beautifully and 'atitvout' works splendidly, but the high resolution makes text on the TV screen tooooo small.  When I try to switch resolutions to 800x600, both the LCD and my TV connected via s-video are scrambled.  I've messed with my various sync settings in xorg.conf and also tried a Modeline I generated with some specs I found for the display all to no avail.  

I tried going back to the feisty live CD with 'safe mode' video.  Even then 1024x768 loads fine, but 800x600 is scrambled! 

Any suggestions on things to tinker with?  I'm so close to having things perfect I can taste it.

---

