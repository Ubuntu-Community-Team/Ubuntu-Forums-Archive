---
title: "Toshiba L350 Webcam Problem"
date: 2009-03-27
forum: Hardware
---

### Post by canclan on 2009-03-27
I have spent days trying to figure this one out, so any help would be greatly appreciated.  

I just bought a Toshiba Satellite L350-038 for my Dad, who is pretty new to computers, so everything has to be worked out before I send it to him 2000km away!  It has a built in webcam.  After giving up trying to get Vista to relinquish more space for a dual boot, I wiped the drive and installed Intrepid.   To my astonishment, everything worked!  Or so I thought.  The webcam appears to work in Ekiga and Skype (in self view), but when I Skype video call *my* computer (XP) with the webcam, the video from the Toshiba is more like a still shot every 10 to 20 seconds.  Almost no streaming.  The Toshiba can receive video fine.  

I can not find anything on the forums (or net) about a problem like this (too new?), and everything (including sound) works fine.  Webcam problems seem to be about getting no picture, not *some* picture.  It is almost like there is something limiting the transfer between the webcam and the uploading wifi (which is only most of the os!).  
FYI:  (speedtest.net) dl speed 4.08 MB/s & ul speed 440 kb/s.

Any ideas or suggestions?  I can list any outputs that might help.



PS Regardless, I am *super* impressed that a brand new laptop works "out of the box" with Intrepid!

---

### Post by canclan on 2009-04-07
So, as an FYI for anyone else who comes across this thread, I tried the following without success:

Retried skype for linux (cheese still worked but I could not get Ekiga to work/connect either);
I tried most recent Chicony drivers, both open and propriety;
I tried Virtualbox with XP - skype kept crashing and no video;


In the end (~20hrs), I made the laptop a dual boot with XP and Intrepid, downloaded the XP webcam drivers from Toshiba Europe, and everything worked fine.

Hopefully someone will eventually get this built-in webcam to work properly with Ubuntu/Intrepid since everything else seemed to work fine.  Also, FYI, if you try to setup dual boot on this machine and get a BSOD right before you get to install XP from the boot disk, all you have to do is go into BIOS and change the hard drive controller to "Compatibility".  XP install disk does not have the USB SATA driver on it.  Install works after that.  

FYI and good luck.

---

