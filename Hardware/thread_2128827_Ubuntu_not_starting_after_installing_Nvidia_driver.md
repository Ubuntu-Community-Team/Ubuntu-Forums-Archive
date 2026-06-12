---
title: "Ubuntu not starting after installing Nvidia drivers"
date: 2013-03-24
forum: Hardware
---

### Post by markusb on 2013-03-24
Hi all

I've been trying to install the proprietary nvidia drivers for Ubuntu and Ubuntu fails to start.  I am running Ubuntu 12.04 64 bit on a dual boot system with Windows 7 64 bit. My system is an intel i5 64 bit system and my graphics card is a GeForce GTX 660. I have tried using apt-get install nvidia-current nvidia-settings, when I do that I just get a black screen with a blinking cursor when I boot (I get past the grub menu). I've also tried the nvidia drivers downloaded from their site, the file NVIDIA-Linux-x86_64-310.40.run, this runs fine but when I reboot it gets as far as the Unbuntu splash screen then stops. I have removed the xorg.conf file, I have also tried add-apt-repository ppa:xorg-edgers/ppa but I get an error saying 'Could not resolve launchpad.net'. I have scoured the internet, and this forum, for solutions and am getting desperate. I want the proprietary drivers because I want to install CUDA at some point and would prefer to stick with official nvidia drivers as much as possible to try to avoid compatibility problems. I also want to stick with 12.04 for because it is a supported build, though I would go to 12.10 if it's the only way to solve this. Does anyone have any suggestions? I would be so grateful.

Many thanks

Mark

---

### Post by grahammechanical on 2013-03-24
If someone was to download 12.04 today they would not get 12.04. They would get 12.04.2. What is the difference? For one thing the original Ubuntu 12.04 uses Linux kernel 3.2.0. Whereas, Ubuntu 12.04.2 uses Linux kernel 3.5.0 as does Ubuntu 12.10. Is your installation more than six months old? You may not need to install 12.10 but 12.04.2.

I have no idea if this will be the solution. It may be that the kernel in your 12.04 is not supported by the Nvidia 310 driver. Or the other way around. I always think it best that we use Additional Drivers to install proprietary video drivers.

Regards.

---

### Post by markusb on 2013-03-25
Hi grahammechanical, Thanks for your reply. The installation is very new, I downloaded it last week, so it's probably 12.04.02. I'll look into that, maybe it is the problem. And, yes perhaps I should have used Additional Drivers. I wasn't sure if it would use the proprietary drivers which is why I didn't use it.

---

### Post by Bashing-om on 2013-03-25
markusb; Hi !
To verify the version, terminal code:
```
lsb_release -a
``` just so you know.[INDENT=3]
just see'n what I can do to help

[/INDENT]

---

