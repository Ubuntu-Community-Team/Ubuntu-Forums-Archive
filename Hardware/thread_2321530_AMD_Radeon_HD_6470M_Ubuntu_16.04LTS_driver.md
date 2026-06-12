---
title: "AMD Radeon HD 6470M Ubuntu 16.04LTS driver"
date: 2016-04-22
forum: Hardware
---

### Post by Christopher_Calmes on 2016-04-22
Here is the grep output for my card 
```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760] (prog-if 00 [VGA controller])

```

I'm running Lubuntu 16.04 LTS on my HP elitebook 8460p with the AMD Radeon HD 6470M graphics card. In my previous version of 15.10, the card was detected by the addition driver program, but now it's not.
[IMG]http://i.imgur.com/mv5y8NT.png[/IMG]

I see the driver for Ubuntu on AMD's website, but it seems that the last supported version is 14.04 LTS. Is there an  alternate driver that I can install and how would I go about it?
 [URL="http://support.amd.com/en-us/download/desktop/previous/detail?os=Ubuntu%20x86%2064&rev=15.9"]http://support.amd.com/en-us/download/desktop/previous/detail?os=Ubuntu%20x86%2064&rev=15.9



[/URL]

---

### Post by grahammechanical on 2016-04-22
If you are looking for AMD proprietary video drivers then they do not exist in 16.04. The AMD drivers do not work well with the version of the Xserver that is in 16.04

> The fglrx driver is now deprecated in 16.04, and we  recommend its open source alternatives (radeon and amdgpu). AMD put a  lot of work into the drivers, and we backported kernel code from Linux  4.5 to provide a better experience. 


When  upgrading to Ubuntu 16.04 from a previous release, both the fglrx  driver and the xorg.conf will be removed, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware). 


More information is available at [https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Regards

---

### Post by Christopher_Calmes on 2016-04-22
Which of those open source drivers is reccomended and how do I Install it? As you can see fromt the screenshot,my device installed a strange intel proprietary driver. My framerate for glxgears is only about 300 which is pretty low. I don't believe that graphics are being accelerated.

---

### Post by Christopher_Calmes on 2016-04-23
bump

---

### Post by redguy41 on 2016-04-23
THe same thing is on my system, but I'm using hybrid graphics - onboard Intel for powersaving and an accelerator ATI similar to yours. But my VGA default is Intel, and ATI is listed in lspci as display controller. Additional drivers list the same thing. How can I use the ATI card, or make it default? in 14.04 LTS I could use the ATI catalyst and manually switch the cards.

Any help?

---

### Post by Christopher_Calmes on 2016-04-23
Should I just downgrade to 14.04?

---

### Post by Superdarion on 2016-04-27
The correct driver for your card is already selected by the Kernel (as you can read in the excerpt posted by grahammechanical). If you need something specifically from fgrlx, you will have to downgrade for now.

---

