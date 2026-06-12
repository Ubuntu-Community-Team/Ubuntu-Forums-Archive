---
title: "Laptop fan always on in Ubuntu 10.04"
date: 2010-05-12
forum: Hardware
---

### Post by zeiger on 2010-05-12
Hey guys,
I installed Ubuntu 10.04 recently on my Gateway (Acer) ID58 laptop.
It came pre-installed with Windows 7 and so I have not yet removed it, I use dual boot.
When on Windows (very rarely nowadays), I notice that my laptop fan stops frequently in order to reduce battery consumption, when not running high performance applications.
But in Ubuntu, the fan keep going on and on, even when I am just browsing over the Internet. This results in the battery getting discharged very quickly (3 hours, but on Windows, it takes about 5!).
So I was wondering if there is something that I am missing. Is there some power saving mode or some way to make sure the fans work only when required and not all the time?

Thanks!
Zeiger

---

### Post by dino99 on 2010-05-12
install acerhk-source, thinkfan, powernowd

fancontrol and lm-sensors might be already installed

sudo apt-get update
sudo apt-get install -f

sudo update-pciids && update-usbids

sudo dpkg --configure -a

sudo dpkg-reconfigure powermgmt-base

---

### Post by russianbandit on 2010-05-12
I've got the same problem (HP dv4t laptop) and tried the above method, but it didn't help. As soon as the laptop boots the fan keeps spinning in the background in an annoying little hum.

---

