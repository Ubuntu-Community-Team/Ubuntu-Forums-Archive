---
title: "Nvidia dont work i fallow the instructions under 5.10"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by JOKe on 2005-11-17
hi 
i try fallowing the instructions for Ubuntu Guide for ver 5.10
i make 
apt-get install nvidia-glx and nvidia-settings.
i try to make nvidia-glx-enable ( or somethink like this ) no print messege has been showed... when i try to start X i still doesnt have the nvidia drivers installed
i try to edit xorg.conf and comment dri and etc.
i make nv to nvidia
startx - the x dont want to start it says problem in xorg conf.

when this is happened i go to download the nvidia drivers from nvidia.com
i install linux-source-2.6.12 i install linux-image-2-6.12-9-k7 i install linux-headers-2.6.12-9-k7 reboot to kernel 2.6.12 for k7 and start sh nvidia-installer 
it says that i dont have gcc i say OKKKKKK
apt-get install gcc
apt-get install libc
apt-get install libc6 .. i think this was all. oo libx-dev or somethink like this too.
so i start installer again
the installer says that the kernel has been build with a gcc version older than mine .. ( mine is 4.0 maybe kernel is build with 3.4 ) . but i say OKI never mind gogogo.
and he say
Unable to run Ko module bla bla bla ... :(

---

