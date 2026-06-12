---
title: "Nvidia driver not recognized by Ubuntu 16.04 on Lenovo W550s"
date: 2016-12-11
forum: Hardware
---

### Post by ahood on 2016-12-11
Hello,

Installing Nvidia driver on an Lenovo W550s is a frustrating experience. I have installed what is supposed to be a compatible Nvidia driver version (375.x) from ppa as well as from .run file with same non-working result. However, the system doesn't seem to recognize the driver (stuck on Intel). 
This issue is not new for this supposedly compatible laptop, see [nVIDIA Quadro K620M undetected in Thinkpad W550S]("https://ubuntuforums.org/showthread.php?t=2296791&highlight=nvidia+lenovo+w550s"). This post does not report a solution that I have any confidence that will actually work. Also, I prefer not to install bumblebee.

Specifically, I can install the driver but unable to start nvidia-settings because it complains that the driver is not in use and recommends running nvidia-xconfig; however, this command does not resolve the issue. 

The most successful I got was installing the nvidia driver from ppa; however, the system would only boot at 640x480 resolution and not allow changing to a higher resolution.

After spending hours of installing and re-installing nvidia drivers, I am about to give up on Ubuntu. Although there are plenty of how-to's on installing nvidia drivers, none of them have resolved my issue. The only solution I have come up with is installing a non-distribution, in case this is an ubuntu issue. 

If anyone has some info that might shed some light on what I can do next to successfully install nvidia over the next day or two, I will appreciate the reply.

DrH

---

