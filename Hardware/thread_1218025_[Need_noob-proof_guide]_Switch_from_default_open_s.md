---
title: "[Need noob-proof guide] Switch from default open source ATI driver to RadeonHD"
date: 2009-07-20
forum: Hardware
---

### Post by DEagleson on 2009-07-20
Running RadeonHD and getting max 5196 frames in 5.0 seconds = 1039.026 FPS in glxgears with my ATI Mobility Radeon X1600. ;)

Hi, im been using Ubuntu 9.04 for a while now and im quite happy with how responsive my notebook feels.
But i also want to use 3D apps and games and i know that my [ATI Mobility Radeon X1600]("http://en.wikipedia.org/wiki/Radeon_R520#X1600_series") card is considered a "[Legacy Card]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.7lang=English")" by AMD so using their driver is out of question, but i heard that the open source [RadeonHD]("http://wiki.x.org/wiki/radeonhd") may work and give some 3D acceleration.
But i followed the stuff described [here]("https://help.ubuntu.com/community/RadeonHD") and then when i finally restart my system my only choice of GUI is basic 2D.

I have now reinstalled Ubuntu 9.04 x64 and my question now is:
Does someone here know of a Linux noob-proof way to get it to work?

---

### Post by komputes on 2009-07-20
I don't think the open source driver does 3D on all cards. Could you upload /var/log/Xorg.0.log to see what driver is being used. As well please attach the lspci.txt file in your home directory after running this command:
```

lspci -vvnn > ~/lspci/txt
```

---

### Post by DEagleson on 2009-07-20
Okay, found it and zipped it.
And thanks for replying to my thread. :)

---

### Post by Stephyslefthand on 2009-07-20
> **DEagleson said:**
> Hi, im been using Ubuntu 9.04 for a while now and im quite happy with how responsive my notebook feels.
But i also want to use 3D apps and games and i know that my [ATI Mobility Radeon X1600]("http://en.wikipedia.org/wiki/Radeon_R520#X1600_series") card is considered a "[Legacy Card]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.7lang=English")" by AMD so using their driver is out of question, but i heard that the open source [RadeonHD]("http://wiki.x.org/wiki/radeonhd") may work and give some 3D acceleration.
But i followed the stuff described [here]("https://help.ubuntu.com/community/RadeonHD") and then when i finally restart my system my only choice of GUI is basic 2D.

I have now reinstalled Ubuntu 9.04 x64 and my question now is:
Does someone here know of a Linux noob-proof way to get it to work?

My solution was simple and foolproof. I simply left the ATI as it was. I found that whenever I tried to install the ubuntu proprietary extra, it crashed. And as you, had to restart. My server doesnt need gaming grade graphics and resolutions, so I will do without the 3d. 8)

---

### Post by DEagleson on 2009-07-20
> **Stephyslefthand said:**
> My solution was simple and foolproof. I simply left the ATI as it was. I found that whenever I tried to install the ubuntu proprietary extra, it crashed. And as you, had to restart. My server doesnt need gaming grade graphics and resolutions, so I will do without the 3d. 8)

I wish i could do that too, but i really wanna do console emulation and both Mupen64plus [ N64 ] and Dolphin [ Gamecube / Wii ] need 3D acceleration to work at full speed.

---

### Post by DEagleson on 2009-07-20
Sorry but im bumping the thread.

---

### Post by komputes on 2009-07-20
The log file shows that you are using the radeon driver and that your hardware is a ATI Technologies Inc M56P [Radeon Mobility X1600] [1002:71c5]

I can see that there was a fix related to the xserver-xorg-video-ati package in version 1:6.12.2-2ubuntu1 as mentioned in this bug:
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/371279](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/371279)

Please post the output of the following command to see what version you are running:

dpkg -l xserver-xorg-video-ati

I would also recommend reducing the desktop size progressively to see if there is a resolution which treats 3D properly

---

### Post by komputes on 2009-07-21
> **komputes said:**
> 

Please post the output of the following command to see what version you are running:

dpkg -l xserver-xorg-video-ati


You sent me this by private message:

xserver-xorg-video- 1.2.5+git20090710.b X.Org X server -- AMD/ATI r5xx, r6xx display driver

I have 1:6.12.1-0ubuntu2 on jaunty.
The bug above states version 1:6.12.2-2ubuntu1 fixes some issues.

Doing a google search I found a PPA with this version:
[https://launchpad.net/~bdrung/+archive/backports](https://launchpad.net/~bdrung/+archive/backports)

---

