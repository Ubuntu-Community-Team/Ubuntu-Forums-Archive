---
title: "Is nouveau forcibly used by default in 14.04.3?"
date: 2015-08-21
forum: Hardware
---

### Post by Petko_Marinchevski on 2015-08-21
Last winter I installed Ubuntu 14.04.1 and then 14.04.2, both were clean installs, not upgrades. On the installation step about third party software and whether to download additional software (drivers) during installation, I've always checked both boxes and once the installation has finished the proprietary Nvidia drivers were installed. And that was great.

Yesterday I clean installed 14.04.3, checked the same boxes as I always do, but after the installation was finished and I logged in, no NVIDIA driver was installed. I had to use the hardware tab in Software & Sources to install it. I hate that tab because all is done in the background and no info how the installation is going is presented. I mean something like terminal output would be nice.

My laptop has an Nvidia GTX 560M if that's relevant.

My question is, if there has been some policy change in the installer or in the Canonical philosophy, to enforce the use of the free nouveau driver, although the user has checked in the installer that a proprietary driver is desired to be installed?

10x.

---

### Post by ajgreeny on 2015-08-21
Not sure about the enforcement of use of the nouveau driver, nor can I tell you if there has been any change in policy, but it is certainly installed by default even if there are no nvidia cards present in the machine.

If you don't install proprietary drivers during installation, then the nouveau driver will, of course, be used by default, but I had always assumed that the proprietary driver would be the driver in use if it was installed.  I have never had an nvidia card to know more about this, so others may have more detailed info.

---

### Post by Petko_Marinchevski on 2015-08-21
> **ajgreeny said:**
> Not sure about the enforcement of use of the nouveau driver, nor can I tell you if there has been any change in policy, but it is certainly installed by default even if there are no nvidia cards present in the machine.

If you don't install proprietary drivers during installation, then the nouveau driver will, of course, be used by default, but I had always assumed that the proprietary driver would be the driver in use if it was installed.  I have never had an nvidia card to know more about this, so others may have more detailed info.

I guess I have to change the title of the thread then. Thanks for your answer.

---

### Post by dino99 on 2015-08-21
To get the latest nvidia driver available for your installtion, activate that ppa, update, install the nvidia-xxx package, then deactivate the ppa
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

then go to 'additional drivers' to select it, and reboot to get it activated

note: both nvidi-xxx and 'nouveau' can be installed , there is no conflict between them, the system automaticaly blacklist the driver you have not selected for activation

---

### Post by mc4man on 2015-08-21
I've only checked that option a couple of times in the past, don't recollect nvidia drivers being installed but if you say so then I guess it could do so.
(though the option is worded to imply just mp3 support & when there are multiple nvidia driver options available how would one know if best/proper one was being used.

Anyway for 14.04.3 it could be that no nvidia drivers that would build on 14.04.3's kernel were available for 14.04 until the last moment. Maybe it (installing them) was turned off & never restored once it could work...

---

### Post by Petko_Marinchevski on 2015-08-21
> **dino99 said:**
> To get the latest nvidia driver available for your installtion, activate that ppa, update, install the nvidia-xxx package, then deactivate the ppa
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

then go to 'additional drivers' to select it, and reboot to get it activated

note: both nvidi-xxx and 'nouveau' can be installed , there is no conflict between them, the system automaticaly blacklist the driver you have not selected for activation

C'mon, man! Read the OP first, don't asume you know what the thread is all about.

I have no problems with the repo driver, just want to understand why it got installed during installation in 14.04.1 & 14.04.2 after checkmarking the aforementioned boxes, and why it didn't in 14.04.3 despite checkmarking the same aforementioned boxes.

---

### Post by howefield on 2015-08-21
> **Petko_Marinchevski said:**
> I mean something like terminal output would be nice.

Then use it.

---

### Post by Petko_Marinchevski on 2015-08-21
> **mc4man said:**
> I've only checked that option a couple of times in the past, don't recollect nvidia drivers being installed but if you say so then I guess it could do so.
(though the option is worded to imply just mp3 support & when there are multiple nvidia driver options available how would one know if best/proper one was being used.

Anyway for 14.04.3 it could be that no nvidia drivers that would build on 14.04.3's kernel were available for 14.04 until the last moment. Maybe it (installing them) was turned off & never restored once it could work...

There are two checkboxes, one saying "Download additional software" and a second one saying "Install 3rd party software, etc.". Or something close enough.

The first implies graphic drivers, while the second is for mp3, fluendo. The second basically installs ubuntu-restricted-addons package.

---

