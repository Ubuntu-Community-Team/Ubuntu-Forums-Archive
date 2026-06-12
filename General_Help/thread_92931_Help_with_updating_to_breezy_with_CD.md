---
title: "Help with updating to breezy with CD"
date: 2005-11-20
forum: General Help
---

### Post by tman_ubuntu on 2005-11-20
Q1:
I would like to update to Breezy from Hoary using the installation CD.  Right now, I'm hesitant to do so because Breezy won't recognize my nvidia card.  Hoary recognized it flawlessly however Breezy didn't even set up proper screen resolutions.:( 

Usually this is no problem because I would just run xconfig.  Breezy however doesn't seem to install the Xorg configuration binaries.  How do I setup my video card using Xorg?

Q2:
How do I upgrade from Hoary to Breezy using the installation CD?  When I insert the CD, a dialog pops up and ask to start my package manager.  What to do from here?

---

### Post by tman_ubuntu on 2005-11-20
bumpity :D

---

### Post by kperkins on 2005-11-20
Before you upgrade make a copy of /etc/X11/xorg.conf
ie. sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
(or just copy it to a floppy or something probably your best bet.)
Q2:
reboot your computer.  That'll start the upgrade/install process.

---

### Post by aysiu on 2005-11-20
[QUOTE=tman_ubuntu]Q1:
I would like to update to Breezy from Hoary using the installation CD.  Right now, I'm hesitant to do so because Breezy won't recognize my nvidia card.  Hoary recognized it flawlessly however Breezy didn't even set up proper screen resolutions.:( [/quote] I don't see any reason for you to upgrade from Hoary if Hoary works and Breezy doesn't.

> 
Usually this is no problem because I would just run xconfig.  Breezy however doesn't seem to install the Xorg configuration binaries.  How do I setup my video card using Xorg? What do you mean by Breezy not installing the xorg configuration binaries?

> 
Q2:
How do I upgrade from Hoary to Breezy using the installation CD?  When I insert the CD, a dialog pops up and ask to start my package manager.  What to do from here? Upgrade or do a fresh reinstall? I would imagine you'd back up your /etc/apt/sources.list ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` Then edit your /etc/apt/sources.list ```
sudo gedit /etc/apt/sources.list
``` and delete everything but put this one line in ```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
``` Save the file and then type this in ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

