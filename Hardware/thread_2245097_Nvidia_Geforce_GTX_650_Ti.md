---
title: "Nvidia Geforce GTX 650 Ti"
date: 2014-09-21
forum: Hardware
---

### Post by Anthony_McTigue on 2014-09-21
Hello Ubuntu World,

I am a new Ubuntu user and already loving it but for one very annoying problem with my NVIDIA Geforce GTX 650 Ti graphics card.  I have read through numerous previous threads on this forum regarding some of the difficulties that other users have had using NVIDIA graphics cards with Ubuntu.  I have tried numerous times to install the latest NVIDIA drivers but each time I do so, the system will not start.  I get a series of error messages during the boot process that disappear before I get to read them properly but do mention something about NVIDIA then Ubuntu drops to a black screen with a flashing curser that does not respond and I need to use the power button to restart the system.  I then have to restore the open source driver using recovery mode.  The other problem I am having is that Ubuntu keeps freezing when play music using Clementine and when I play videos using VLC (both from DVD and hard drive).  The keyboard and mouse do not respond and the last sound plays on a continuous loop.  I have to use the power button to restart the system.  I gather from my research on this forum that this too is due to a graphics card driver issue however as I have already explained, the system won't when the NVIDIA driver is in use.  I also get some odd graphics behaviour in the form of stray dots and lines that flash for a second an then disappear as I open and close programs.  I am also having graphics problems with the YouTube app whereby it flashes between the startup screen and an all blue screen.

The system in question is relatively old and consists of an Intel Core 2 Duo, an ASUS P5B Deluxe motherboard with 4 GB ram and 2 Hard Drives and an NVIDIA Geforce GTX 650 Ti (which I bought new).  I am hoping to use it as a music/video server that I can leave permanently to my television and use a Logitech wirelesskeyboard and touch pad to control it.  The system is dual boot 64 Bit Ubuntu 14.04 and 64 Bit Windows 7 Professional.  The BIOS is up to date and all hardware functions correctly when booted in Windows 7 so I don't suspect any hardware problems.

---

### Post by cigtoxdoc on 2014-09-21
Your killer here is Ubuntu 14.04.  Does not work with older nVidia graphics card.  If you drop back to 12.04, you should be okay.  Otherwise, head for a motherboard/CPU combination that does not use nVidia or AMD/Radeon graphics.  I did the later as PC is used in my business.

John

---

### Post by Vladlenin5000 on 2014-09-21
Please ignore the previous post. It's entirely wrong, no exceptions, nothing salvageable there except the recommendation about integrated graphics for business machines but you don't put a GTX650 Ti in a PC for text processing or spreadsheets, obviously :lolflag:

Even if it was true - it isn't - that *"Ubuntu 14.04 (...) does not work with older nVidia graphics cards" *it would have no bearing in whatever issues you might suffer simply because your card isn't legacy. The suggestion about using 12.04 flies in the face of all logic and reason (yes, it's that ridiculous). If anything, it may need a newer driver than the one tested and for 14.04 - 331.xx - and offered in the additional drivers. That said and before anything else, please test it with the recommended driver version. Post back if you find any issues and we'll troubleshoot from there.  

Good luck!

---

### Post by Anthony_McTigue on 2014-09-22
Thanks for your advice.  I had previously tried updating the driver to version 343.22 released on 18 September 2014 according to the procedure described here [http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404](http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404).

I initally tried usingthe Nvidia 343.22 official installer (Method 1) however the difficulty arose when I got as far as rebooting the system after Step 2 and the system will not boot.  I get the original series of errors get a series of error messages during the boot process followed by the black screen with a flashing curser that does  not respond to keyboard commands.

I restored the open source driver using recovery mode and then tried using the PPA repository (Method 2) as desrcibed at the bottom of the article at the link posted above however, Ubuntu returned an error and aborted the installation.  

I then tried Steps 1 to 2 using and then re-booted into recovery mode to see if I could complete the installation from the root command however I could not access the ~/Downloads directioy (I mounted the file system by executing the fschk command).  

I restored the open source driver again using recovery mode and then tried Method 2 again but this time I dropped to the command console using Cth+Alt+F1.  The driver installation seemed to complete successfully  but then I rebooted and am back to the original problem whereby the system hangs during startup but the difference being that there are no error messages and no flashing curser.

I know it is unlikely to have anything to do with it but though it worth mentioned that I do not have a monitor per say but rather the system is plugged into my Samsung TV via a VGA cable.  May this have anything to do with it?  Would it perhaps make a difference if I used the DVI or HDMI outputs on the NVIDIA Graphics Card?

---

### Post by Vladlenin5000 on 2014-09-22
I suspect you have anther problem in your OS and the issues with the driver are just a symptom. Hopefully I'm wrong...
Have you completely uninstalled - purged - the previous drivers before installing the new ones?  If not - and I bet on that - you're in for all sorts of problems. 
Honestly, I would start over with a fresh install of the OS then just add a PPA for the newer nvidia drivers and install from there, thus avoiding the hassle of a manual installation.

---

### Post by Anthony_McTigue on 2014-09-23
Thanks guys for your advice.  I have through trial and error found an old graphics card driver that has at least provided me with a temporary workaround to solve the booting/freezing problem.  I am currently running NVIDIA legacy binary driver - version 304.123 from NVIDIA-304 (Open Source).  I left my computer running while playing movies for 24 hours straight using VLC media player and it did not freeze and the system boots/shuts down correctly.  

> I suspect you have anther problem in your OS and the issues with the driver are just a symptom. Hopefully I'm wrong...
Have you completely uninstalled - purged - the previous drivers before  installing the new ones?  If not - and I bet on that - you're in for all  sorts of problems. 
Honestly, I would start over with a fresh install of the OS then just  add a PPA for the newer nvidia drivers and install from there, thus  avoiding the hassle of a manual installation.

I do have a second as of yet unused hard drive in my system so what I plan to do is set that as my boot partition and install a fresh version of Ubuntu on that drive and then run the PPA straight after I install it.  If everything boots up and nothing freezes then I guess we'll know for sure whether it is an OS problem or a driver compatibility problem.  I will post the outcome.  Thanks again for the advice.

---

### Post by Anthony_McTigue on 2014-10-04
Well guys, I got around to doing a fresh Ubuntu install on my unusued hard drive and install the latest NVIDIA graphics card driver using the PPA method described at the link above and I am back to a hanging black screen on startup!  Anyone any further ideas?

---

### Post by sns4rnr on 2014-10-04
That latest 343.22 driver I don't think is really for that card... Thats the new one for supporting their new series of cards.From what I see their recommended driver for your card is 340.46.[http://www.nvidia.com/download/driverResults.aspx/78469/en-us](http://www.nvidia.com/download/driverResults.aspx/78469/en-us) Maybe try that.Very curious to see your result.

---

### Post by Vladlenin5000 on 2014-10-04
I'm using 343.22 for a GT630 and it works*.

* With some glitches. Some webpages flicker until I use the scroll, VLC suddenly shows a very thin green bar at the bottom or at the right side or both for certain videos (Kodi Entertainment Center, former XBMC, seems unaffected) and it DIDN'T solve the issue in Euro Truck Simulator 2 I was hopping it would.

---

### Post by sns4rnr on 2014-10-04
Interesting.   Details on 343.22 do indicate it should support 630 and 650Ti,   however if you go to Nvidia's page where you enter your specific model, it directs you to 340.46.   So as with all things Nvidia/Ubuntu....it's clear as mud as to what one should do.

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I'm planning to swap an underpowered Radeon card for a GT630 or GT730 soon so I'm curious to see how this plays out.

---

### Post by Anthony_McTigue on 2014-10-17
Thanks for the tips guys.  Sorry I have not replied yet but it has been a busy week at work so haven't had a chance to check in on the thread.  Will try the suggestions over the weekend and post the results.

---

