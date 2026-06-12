---
title: "Nouveau dirver &quot;disappears&quot; in 14.04.3 with any upgrade GeForce 320M"
date: 2015-09-22
forum: Hardware
---

### Post by maestrobwh1 on 2015-09-22
I am not sure what the heck is going on.  I have tried this 4 times on a late 2010 Mac Air.  The usb key boots fine in EFI mode, installs to a partition fine, boots fine but if any upgrades are done, I get a low graphics mode warning on a reboot but it refused to allow for the use of any x resources, including the trackpad.  
1. The first time, I enabled "install updates" and installed Ubuntu, and it left me with no nouveau driver.  Fine.  I tried to manually install it with apt-get and it gave me dependency errors on other packages for some x crap and said I had held packages which I did not.  Apt-get install -f did not do anything.  Fine.  
2. I installed it a second time, it booted just fine, but when I upgraded, the reboot left me with EXACTLY the same situation.  Tried installing nvidia-304 from recovery, did a nvidia-xconfig, and then ended up with a black screen on reboot, even after adding "nomodeset."  
3. Fine, booted the usb key again and went with "install Ubuntu" and ended up with the first situation. 
4. Reinstalled again using the "try Ubuntu," booted the install, installed synaptic, "locked" all related x packages, upgraded, rebooted and viola, back to situation 1"  There is a terrible issue with something in the repository packages perhaps but even if the xserver-xorg-video-nouveau is locked, it somehow become corrupted if it is not outright somehow removed by the upgrade process. Whaaaaaat?

Unacceptable.  I don't even know how to file a bug because I can't stay long enough on a working system to do so.  I've been working with Ubuntu since 6.06 and this situation is totally bizarre and disappointing.  The nouveau driver works fine with a vanilla install. 

Nvidia GeForce 320M, Macbook air, 3,2 late 2010.  Runs fine on a later model Mac Air that uses the Intel GMA 4000.

---

### Post by maestrobwh1 on 2015-09-23
Partial solution: since I kept getting low resolution message on boot and part of the message suggested it could not configure other input devices so I plugged in a mouse on the next boot AND it brought me to the desktop, with the touchpad also working.  Weird.  I tried to install mtrack, thinking there was an issue with the synaptics driver and my touchpad.  Again, dependency issues.  I saw some info regarding xserver-xorg-core on the internet whereby other x packages had dependency issues once the latest was installed, so I locked that package only, did a full upgrade, then the xserver-xorg-input-mtrack-lts, which is listed TWICE in synaptic under the same name?  One had unmet dependencies, along with the package without the -lts ending.  

 I locked xserver-xorg-core so that dependency errors went away regarding other x packages.  I then was able to install the mtrack package and well, it works now.  This is NOT solved really because there is definitely something going on with the packages in the repo, at least my my combination of needed packages.

---

### Post by maestrobwh1 on 2015-09-23
Partial solution: since I kept getting low resolution message on boot and part of the message suggested it could not configure other input devices so I plugged in a mouse on the next boot AND it brought me to the desktop, with the touchpad also working.  Weird.  I tried to install mtrack, thinking there was an issue with the synaptics driver and my touchpad.  Again, dependency issues.  I saw some info regarding xserver-xorg-core on the internet whereby other x packages had dependency issues once the latest was installed, so I locked that package only, did a full upgrade, then the xserver-xorg-input-mtrack-lts, which is listed TWICE in synaptic under the same name?  One had unmet dependencies, along with the package without the -lts ending.  

 I locked xserver-xorg-core so that dependency errors went away regarding other x packages.  I then was able to install the mtrack package and well, it works now.  This is NOT solved really because there is definitely something going on with the packages in the repo, at least my my combination of needed packages.

---

