---
title: "HDMI output with LiveCD but not following installation"
date: 2014-12-16
forum: Hardware
---

### Post by odhoenator on 2014-12-16
Hi all,

I'm just installed Ubuntu 14.04 on a new machine. The graphics card is a Sapphire Radeon R7 250. I used an HDMI cable throughout the original boot procedure with the LiveCD and the installation itself, but once installation had completed then HDMI output stopped working. I've reverted to a VGA cable for now, but can anyone tell me how to get HDMI output up and running, please? 

I only have a single display, so please bear that in mind - if I end up booted into Ubuntu with the HDMI cable then I will be 'blind', and only able to power down/reboot using the buttons on the computer case (unless you know a better way!) - it is possible to swap between VGA and HDMI cables while the computer is running, but this has a tendency to cause crashes, so I'd prefer to avoid it if possible.

Thanks!

---

### Post by odhoenator on 2014-12-18
OK, I figured it out. I installed the proprietary driver, and this seems to work with the HDMI cable. I had to adjust the overscan in the proprietary control panel software, as decribed here: [http://ubuntuforums.org/showthread.php?t=2064230&p=12270657#post12270657](http://ubuntuforums.org/showthread.php?t=2064230&p=12270657#post12270657)

---

