---
title: "How to exit X Window and install Nvidia driver?"
date: 2011-01-15
forum: Hardware
---

### Post by northfly on 2011-01-15
When I install the nvidia driver for my gtx570, it says I need to exit X Window, how to do this? Thanks.

---

### Post by cchhrriiss121212 on 2011-01-15
In short:
put the driver in your home folder
ctrl+alt+f1
sudo service gdm stop
sudo ./driver
sudo service gdm start

If you are new to Ubuntu, it is better to use the recommended drivers in System>Hardware Drivers.

---

### Post by northfly on 2011-01-15
> **cchhrriiss121212 said:**
> In short:
put the driver in your home folder
ctrl+alt+f1
sudo service gdm stop
sudo ./driver
sudo service gdm start

If you are new to Ubuntu, it is better to use the recommended drivers in System>Hardware Drivers.
Thanks, Is there any configuration after the installation?

---

### Post by northfly on 2011-01-15
What is the difference between a native nvidia driver and the x org driver? performance difference ? a lot?

---

### Post by cchhrriiss121212 on 2011-01-16
There is no config to do after installing, check nvidia-settings if you want to change anything but the defaults are usually the best option. 
> What is the difference between a native nvidia driver and the x org driver?
The driver that comes with Ubuntu is open source but it is less able than the proprietary one created by nvidia. The open driver has no 3d support and does not have any hardware acceleration for video, unlike the closed driver which can use vdpau output with mplayer and flash. 
You will have to remove the open driver before installing the closed driver manually. It is called nouveau and you can remove it via synaptic.

---

