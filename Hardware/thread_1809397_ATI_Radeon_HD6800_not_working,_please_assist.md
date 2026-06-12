---
title: "ATI Radeon HD6800 not working, please assist"
date: 2011-07-21
forum: Hardware
---

### Post by cmccollough on 2011-07-21
Hey guys. I recently installed Ubuntu 11.04. Initially, after installing the proprietary drivers through application drivers I rebooted and got an error saying something to the effect of "your hardware isnt capable of running Unity." I found this odd, due to the fact that I just bought this HP Envy 17 3D.  Anyways, I tried to access the ATI Catalyst Control Center but I get an error: There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

I did some research and found this page:[http://askubuntu.com/questions/46976/ati-catalyst-control-center-gives-error-natty-64bit-radeon-hd-6470m](http://askubuntu.com/questions/46976/ati-catalyst-control-center-gives-error-natty-64bit-radeon-hd-6470m) and followed the sudo commands at the bottom:  
   sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
   sudo apt-get update
   sudo apt-get install fglrx

Upon restarting and attempting to run aticonfig, I now get the response, "No supported adapters connected"

Someone please help, I would really like to take advantage of all the cool 3d stuff.

---

