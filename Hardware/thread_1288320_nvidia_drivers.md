---
title: "nvidia drivers"
date: 2009-10-11
forum: Hardware
---

### Post by balumohan2 on 2009-10-11
HI ALL..
i am using ubuntu 9.1
.i cant start installation process when my Nvidia fx 5200 256mb card is connected....there was some kernal errors...so i completed my installation by removing the graphics card...now i need to install the drivers for nvidia/need to work with it....

but now also when the card is connected i cant boot into ubuntu

please help me

---

### Post by antonkedrov on 2009-10-11
> **balumohan2 said:**
> HI ALL..
i am using ubuntu 9.1
.i cant start installation process when my Nvidia fx 5200 256mb card is connected....there was some kernal errors...so i completed my installation by removing the graphics card...now i need to install the drivers for nvidia/need to work with it....

but now also when the card is connected i cant boot into ubuntu

please help me

Hi, balumohan2 !
can you describe you problem more - what now happens (what you see) when you try to load Ubuntu?
you should download your video drivers for linux from nvidia.com, put file to your home directory for example. file name will be like NVIDIA-Linux-x86-....pkg1.run.
next you should go to console, stop gdm by executing command:
sudo /etc/init.d/gdm stop

then you should install your nvidia driver by:
cd ~
sudo sh [nvidia_driver_filename_here]

proceed setup and when it finish type in console:
sudo /etc/init.d/gdm start

---

### Post by Midnighter on 2009-10-11
I have that exact card, and i have no problem running and installing with it in. What other hardware do you have? Perhaps something is conflicting.

---

