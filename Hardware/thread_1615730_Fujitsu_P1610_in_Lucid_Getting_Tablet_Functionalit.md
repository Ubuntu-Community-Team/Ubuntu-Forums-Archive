---
title: "Fujitsu P1610 in Lucid: Getting Tablet Functionality to Work Correctly"
date: 2010-11-07
forum: Hardware
---

### Post by The Flying Penguin on 2010-11-07
Ok guys. I hate to make to make a new post when there are already a couple other posts on this tablet but they are titled for other Ubuntu versions and are marked solved so I fear they may be overlooked.
 
 I am so close to getting this working correctly. I have tried many different methods and combinations of fixes with no real success.
 
 Currently, I have the touchscreen working, kinda. If I touch somewhere on the screen, I have to wait a second before making another touch or the cursor goes somewhere completely different then where I touch. If I click slowly it seems to work fine. It's almost like it needs a second to reset between touches.
 
 I can finally put the tablet into portrait mode and have the stylus recalibrate, but only when I swivel the screen into tablet orientation. If I flip the screen over, it goes into portrait and I can then start clicking away. That is certainly progress as I couldn't get that to work before. The problem is that a total of four on-screen keyboards pop up. Also, after swiveling, if I rotate the screen into landscape mode by pushing the button, touch calibration does not follow. If I flip the screen back into notebook position, sometimes touch will recalibrate and sometimes it won't.
 
 Here is what I have done:
 
 1) Fresh install Lucid and perform all updates.
 
 2) ```
sudo apt-get remove xserver-xorg-input-wacom
``` 3) Install wacomtools deb: [http://launchpadlibrarian.net/33684766/wacom-tools_0.8.4.1-0ubuntu4_i386.deb](http://launchpadlibrarian.net/33684766/wacom-tools_0.8.4.1-0ubuntu4_i386.deb)
 
4) ```
sudo apt-get install setserial libxt-dev libxtst-dev
``` 

 5) I download the six patched deb files from [http://linuxwacom.sourceforge.net/index.php/dl](http://linuxwacom.sourceforge.net/index.php/dl)
 
I install them in this order:
 fsc-btns-kernel-source_2.1.0-1uk4_i386.deb
fscd_2.1.0-1uk4_i386.deb
fscrotd_2.1.0-1uk4_i386.deb
fjbtndrv_2.1.0-1uk4_i386.deb
libx11-guitest-perl_0.21-1_i386.deb
 fsc-p1610_1.2_i386.deb


6) Restart and then I'm at the point in my description.

Any suggestions?

---

