---
title: "Sound Driver Reinstall Error"
date: 2009-12-15
forum: Hardware
---

### Post by bsouk on 2009-12-15
Hi, 
So a few days ago my sound stopped working all together on my Ubuntu 9.04 system, and since then I did some tinkering with the drivers to try and get it going again. 
I attempted to install pulse audio to avail, and also tried installing alsa-driver-linuxant-1.0.20.3_all.deb
To upgrade my asa drivers. 
None of this seems to be working, so I am now attempting to refresh/reinstall the sound drivers completely. 
I issued this command in terminal:

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2.

The problem was that it could not find packages under my username.
So I then tried this:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
Then:
sudo apt-get install linux-sound-base alsa-base alsa-utils
With these results:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  paprefs pavucontrol pulseaudio-module-zeroconf padevchooser paman
  libgconfmm-2.6-1c2 pavumeter libglademm-2.4-1c2a
Use 'apt-get autoremove' to remove them.
Suggested packages:
  oss-compat
The following NEW packages will be installed:
  alsa-base alsa-utils linux-sound-base
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1345kB of archives.
After this operation, 2605kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package linux-sound-base.
(Reading database ... 181126 files and directories currently installed.)
Unpacking linux-sound-base (from .../linux-sound-base_1.0.18.dfsg-1ubuntu8_all.deb) ...
Selecting previously deselected package alsa-base.
Unpacking alsa-base (from .../alsa-base_1.0.18.dfsg-1ubuntu8_all.deb) ...
Selecting previously deselected package alsa-utils.
Unpacking alsa-utils (from .../alsa-utils_1.0.18-1ubuntu11_i386.deb) ...
Processing triggers for man-db ...
Setting up linux-sound-base (1.0.18.dfsg-1ubuntu8) ...

Setting up alsa-base (1.0.18.dfsg-1ubuntu8) ...

Setting up alsa-utils (1.0.18-1ubuntu11) ...

But still, I have no audio. Can anyone tell me how do just clear my system and start over or what I am doing wrong? I'm not getting sound or mic from anything.

Thanks for your help.

---

### Post by bsouk on 2009-12-15
After that I actually issued this command:
sudo apt-get install gdm ubuntu-desktop

Which removed my esound driver, then rebooted, and it seems to be working...
But I still need help getting my microphone working again now.

---

