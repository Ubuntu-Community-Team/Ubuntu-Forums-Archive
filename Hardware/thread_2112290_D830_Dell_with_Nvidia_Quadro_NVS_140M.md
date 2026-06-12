---
title: "D830 Dell with Nvidia Quadro NVS 140M"
date: 2013-02-04
forum: Hardware
---

### Post by choppedliver on 2013-02-04
Hi folks, I am trying to get version 12.10 64 bit running of Lubuntu running on my Dell d830 core 2 duo  with Nvidia Quadro NVS 140M 256 Megabyte video 

The lubuntu detected driver works, I get my 1680x1050 notebook display, but it doesn't seem very snappy. I think it was the "nouveau" or whatever the open source version of the driver is. I am trying to install these accelerated drivers

[http://www.nvidia.com/object/linux-display-amd64-310.32-driver.html](http://www.nvidia.com/object/linux-display-amd64-310.32-driver.html)


After googling I have tried several things including sudo apt-get install purge nvidia-* , I have installed gcc , make, binutils, and linux-generic-headers. 

When I run the nvidia installer 
sudo ./NVIDIA-Linux-x86_64-310.32.run

"verifying archive integrity ... Ok"

Accept the license

"There appears to be a driver installed on your system, existing will be uninstalled (etc), existing will be uninstalled, want to continue?" 

Yes

"The Distribution-provided pre-install script failed!, continue anyway?" 

If I answer yes, it goes through installation, but the driver doesn't work. When I reboot I get a blue screen with the lubuntu logo and then i get some garbage on the screen around the logo

If anyone can help me install the accelerated driver, I would appreciate it.

---

