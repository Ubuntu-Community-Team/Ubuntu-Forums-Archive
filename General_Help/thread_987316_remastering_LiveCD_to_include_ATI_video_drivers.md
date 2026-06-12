---
title: "remastering LiveCD to include ATI video drivers?"
date: 2008-11-19
forum: General Help
---

### Post by clacker on 2008-11-19
I have been playing around with remastering the Ubuntu 8.10 liveCD and I was wondering if it were possible to install the video drivers so that they were loaded when the CD boots.  I have successfully remastered a few CDs now using the normal remaster process from [https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization"), and I tried the same procedure to load the ATI drivers I need using apt-get inside the chroot environment:

sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo apt-get install dkms fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx

Most of my remasters look just fine and the installed apt-get packages work like they should.  When I start the liveCD with the ATI driver installed, however, my drivers are not working until I load them from System->Administration->Hardware Drivers and I log out/log in and then it stills says that I need to restart.  Naturally, if I restart I loose the drivers I just loaded and they don't seem to be loaded correctly at this point because tux racer doesn't work correctly, although the compiz window effects work correctly so some aspects of the install worked.

Does anyone have any suggestions for how to get the chroot environment to recognize that the drivers are loaded and it's OK to start with these drivers?  This computer will be the only one I use this liveCD with.

---

### Post by wolfen69 on 2008-11-19
have you tried [remastersys]("http://www.remastersys.klikit-linux.com/")? i have not tried it with video drivers installed, but it remembered everything else.

---

### Post by clacker on 2008-11-19
I did try remastersys.  You're right, it worked great, everything worked but the video drivers.  I should mention I tried remastersys from the liveCD because I really can't install to my hard drive until I'm 100% sure everything will work.  I bought a Western Digital USB drive, thinking to install to that and then use remastersys, but ubuntu 8.10 doesn't let me install to that drive, either as a usb install or hard drive install.

---

