---
title: "Hardware Driver for integrated Intel GMA 4500WHD on Thinkpad W500?"
date: 2010-11-17
forum: Hardware
---

### Post by allbread on 2010-11-17
I am attempting something similar to the following:

[http://ubuntuforums.org/showthread.php?t=1292723&highlight=w500](http://ubuntuforums.org/showthread.php?t=1292723&highlight=w500)

In the link above the author mentions the "xserver-xorg-video-intel 2:2.9.0-1ubuntu1"  for the integrated Intel GMA 4500MHD... is it necessary to install this  separately in 10.10 or is it included in the package?

The reason I ask is that, when running on  the integrated gpu, if I bring up the "hardware drivers" panel no  proprietary drivers are listed...

Should I look to install the latest version of the "xserver-xorg-video-intel" driver or is it installed by default? 

Thanks!

---

### Post by dino99 on 2010-11-17
open synaptic to check its installation (you need it of course)

to get the latest driver, add this ppa to synaptic repo tab:

ppa:ubuntu-x-swat/x-updates

( from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) )

then update

the wrong low resolution might be due to a weird xorg.conf, remove it (actual kernel directly deal with X anyway):

sudo rm -f /etc/X11/xorg.conf

then reboot

---

### Post by allbread on 2010-11-17
Thanks for the info - should it make any difference if I am using Linux Mint 10 (based on Ubuntu 10.10 as I understand)?

---

