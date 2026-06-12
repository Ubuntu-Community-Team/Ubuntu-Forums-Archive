---
title: "Ati Radeon 9250 problems with 9.10"
date: 2009-12-27
forum: Hardware
---

### Post by PredatorOC on 2009-12-27
After updating from Ubuntu 9.04 to 9.10, desktop effects stopped working and video playback became very choppy. Especially when viewing in full screen. I tried Kubuntu 9.10 from the CD and it had similar problems.

I tried installing Ati's own driver, but it kept complaining that it couldn't locate X server. I tried installing build-essential, but it didn't help.

Xorg.conf was all on default, with no mention of what driver it is using or anything else specific for that matter.

The computer is an Acer Aspire T135 desktop.

Any suggestions on how to proceed?

---

### Post by lidex on 2009-12-27
Run these commands in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm /etc/X11/xorg.conf
```

Now reboot!

Up again? Run this command and post output:
```
uname -r
```

---

### Post by MeanEYE on 2009-12-27
This is all fishing in the dark and I doubt removing xorg.conf would help. ATI drivers don't support 9250 anymore. You will have to install legacy drivers xserver-xorg-video-radeon. 

Do a ```
apt-cache search fglrx
```
And remove everything except jockey. 

Make sure you also rename or remove /etc/ati directory (if it exists).

Remove xorg.conf (or restore ti from xorg.conf.failsafe)...

Then try installing xserver-xorg-video-radeon

---

