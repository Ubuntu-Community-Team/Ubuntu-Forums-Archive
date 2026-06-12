---
title: "Unable to remove libdrm-nouveau2"
date: 2015-02-16
forum: Hardware
---

### Post by gigurra on 2015-02-16
I'm going to make another attempt at getting nvidia drivers up and running again, but first, I want remove the nouveau one.
I think I've managed to uninstall all nouveau-related packages except libdrm-nouveau2. When I try to remove it, I get some wierd dependency errors.

Anyone got an idea of what the following could mean?
I'm on a fairly newly installed 14.04 (two days ago), and this is one of the few things I haven't got working 100% yet.

>>> sudo apt-get remove libdrm-nouveau2 


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 account-plugin-facebook : Depends: libaccount-plugin-generic-oauth but it is not going to be installed or
                                    ubuntu-system-settings-online-accounts but it is not going to be installed
 indicator-bluetooth : Depends: unity-control-center but it is not going to be installed or
                                gnome-control-center but it is not going to be installed or
                                ubuntu-system-settings but it is not going to be installed
 libqt5gui5 : Depends: libegl1-mesa (>= 7.8.1) or
                       libegl1-x11
              Depends: libgbm1 (>= 8.1~0) but it is not going to be installed
              Depends: libgl1-mesa-glx or
                       libgl1
 libqt5multimedia5-plugins : Depends: libqgsttools-p1 (>= 5.2.1-0ubuntu5) but it is not going to be installed
 libqt5quick5 : Depends: libgl1-mesa-glx or
                         libgl1
 libubuntu-application-api-mirserver1 : Depends: libmirserver18 (>= 0.1.8+14.04.20140408.1) but it is not going to be installed
 libunity-mir1 : Depends: libmirserver18 (>= 0.1.8+14.04.20140411) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by Yellow Pasque on 2015-02-16
DO NOT remove libdrm-nouveau2 (or apt will want to remove all libdrm packages). It's not necessary to remove any nouveau packages. 
The only part of nouveau that may conflict with the proprietary driver is the kernel module. When you install the nvidia package, it will take care of blacklisting the nouveau kernel module for you.

---

### Post by efflandt on 2015-02-16
I can confirm what [COLOR=#000000]Temüjin says. I have been running various versions of Ubuntu using nvidia graphics on my current PC for at least 5 years and have never had to do anything about nouveau (except using **nomodest** boot parameter in some cases)[/COLOR] when installing Ubuntu nvidia packages. The nvidia-current (304) version was too old to support my new GTX 750 Ti. It worked fine with nvidia-331, but I am now using nvidia-346 from xorg-edgers ppa to play around with video overclocking.

I heard that nomodeset could muck up installing 14.04.1 with hybrid Intel/Nvidia graphics, so I did not even use that boot parameter for recent live/install to mSATA SSD on my laptop. I simply installed Ubuntu (just modifying a couple of files related to SSD after that) and after rebooting installed nvidia-331-updates package which was the one recommended for my laptop. That appears to be working fine.

But what nvidia graphics card/chip do you have? I have seen some people strangely attempting to install nvidia drivers who "only" have Intel video, without any nvidia card or chip at all. All that could do is make their system not work properly if anything nvidia specific is in their xorg.conf.

PS: If you have a very old nvidia card it might not work with current nvidia drivers and old enough nvidia drivers might no longer be available or easy to use. Even Ubuntu 12.04 required some work arounds to use very old nvidia drivers. In that case nouveau may be the best that you can do.

---

