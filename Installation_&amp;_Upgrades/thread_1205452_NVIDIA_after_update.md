---
title: "NVIDIA after update"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Sin@Sin-Sacrifice on 2009-07-06
So I&#7743; sitting here about 2 weeks ago and see theres an update for nvidia so I get it. Just the factory ubuntu driver was installed and thats what updated. I reboot and wouldnt you know that the fargin driver isnt going to let me use compiz. I thought the driver might fix the reigning problems with all of the x tools crashing the system periodically. Anyway I tried to remove everything nvidia and reinstall and now I&#7743; getting this ```
E: /var/cache/apt/archives/nvidia-glx-180_180.11-0ubuntu1~intrepid1_i386.deb: subprocess pre-installation script returned error exit status 2
``` error for every version. I&#7743; about ready to delete everything that even says nvidia and start again so I, hopefully, wont have to reinstall ubuntu and have to re-transfer 125GB of media for the 3rd time since building this system (all thanks to letting the wrong people touch it). Yes... I am frustrated. Anyone know what that error is all about?

---

### Post by merlinus on 2009-07-06
I got rid of the nvidia drivers this way:

```
sudo nvidia-uninstall
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install xserver-xorg-video-all
```Restarted and installed the 180.44 driver via System/Administration/Hardware Drivers,
restarted again, ran
```
gksu nvidia-settings
```to configure my card and all desktop effects are working.

---

