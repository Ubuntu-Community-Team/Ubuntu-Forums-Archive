---
title: "Bison webcam not working in Ubuntu 13.04 (online upgrade)"
date: 2013-05-29
forum: Hardware
---

### Post by Bill Tetzeli on 2013-05-29
Hey all,


   I just noticed that my Bison webcam has stopped working again.  I tried booting back into every earlier kernel version I could (going all the way back to 3.5.0-27-generic) and I get the exact same message every time I try to start up guvcview:


"Guvcview error:


Unable to open device


Please make sure the camera is connected
and that the correct driver is installed."


I also reinstalled the System 76 drivers on my Pangolin Performance and restored the computer to factory state, but still no soap.  Any ideas, or is this a bug that still needs to be fixed?

TIA

Bill

---

### Post by Bill Tetzeli on 2013-05-30
Okay, sorry for the false alarm.  I just figured out what's broken.

Me.

I accidentally typed Fn + F10 when trying to increase the screen brightness, which instead turned off the webcam.  Of course, I only discovered this after backing up my home directory and restoring a 2 month-old backup so now I'm back at Ubuntu 12.10.  So now it's another few hours before I get the home folder restored (100s of GBs of music) and the system reupdated/reupgraded.  Sorry for crying wolf.

---

