---
title: "6800xt not working like it should on 10.04"
date: 2010-05-07
forum: Hardware
---

### Post by frank8880 on 2010-05-07
hey guys, i installed the latest version of ubuntu, 10.04, 2 days ago and after a while i was able to configure the wifi and all that... now my problem is with my video card i mean, the OS automatically downloaded the drivers so i could setup the right resolution for my screen: 1280x1024.

but the problem is when playing fullscreen videos, i see horizontal frames, refreshing, like when a video card is not properly installed, like in Windows, something that's supposed to be fixed after it has its proper drivers. i, however, downloaded the latest drivers from nvidia.com and was able to install them but still, i feel like my video card is lacking the performance it has on Windows.

here are my pc specs ( yes i know, old ):

CPU Athlon 64x2 4000+ socket am2
Motherboard ASUS M2N SLI-DELUXE
Video XFX 6800XT PCI-E

any help would be greatly appreciated

---

### Post by frank8880 on 2010-05-07
bump?

---

### Post by frank8880 on 2010-05-08
somebody, help pls

---

### Post by dino99 on 2010-05-08
system admin hardware driver: nvidia-current activated ?

---

### Post by frank8880 on 2010-05-08
> **dino99 said:**
> system admin hardware driver: nvidia-current activated ?

should i input that command just like that? and see what it does?

---

### Post by khelben1979 on 2010-05-08
What driver version did you download? Also, did you follow the installation instructions?

---

### Post by frank8880 on 2010-05-08
> **khelben1979 said:**
> What driver version did you download? Also, did you follow the installation instructions?

i installed: LINUX X64 (AMD64/EM64T) DISPLAY DRIVER
 
 

Version:
195.36.24 Certified
Release Date:
2010.04.28
Operating System:
Linux 64-bit
Language:
English (U.S.)
File Size:
40.1 MB


basically there is no installation instructions other than:

> sh ./NVIDIA-Linux-x86-195.36.24-pkg2.run

ADDITIONAL INFORMATION
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.

Also note that SuSE users should read the SuSE NVIDIA Installer HOWTO before downloading the driver.

Installation instructions: Once you have downloaded the driver, change to the directory containing the driver package and install the driver by running, as root, sh ./NVIDIA-Linux-x86-195.36.24-pkg2.run

One of the last installation steps will offer to update your X configuration file. Either accept that offer, edit your X configuration file manually so that the NVIDIA X driver will be used, or run nvidia-xconfig

See the README for more detailed instructions.

---

### Post by khelben1979 on 2010-05-09
Post your X configuration file which you'll find here: > /etc/X11/xorg.conf

---

