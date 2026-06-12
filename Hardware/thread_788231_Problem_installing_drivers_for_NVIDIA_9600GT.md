---
title: "Problem installing drivers for NVIDIA 9600GT"
date: 2008-05-09
forum: Hardware
---

### Post by ali999 on 2008-05-09
Hi

I recently had to reinstall Ubuntu on my computer because I messed up my boot file trying to set up something. Anyways, after reinstalling I tried to install the drivers for my video card which is an Nvidia 9600GT. I have done this before successfully and was using the same method to install again but I am having some issues. From previous experience I know that the driver installation is going to ask me for libc headers so I have to run the command ```
sudo apt-get install build-essential xorg-dev pkg-config linux-headers-$(uname -r
``` and then stop gdm by ```
sudo /etc/init.d/gdm stop
```. However when I run the first command,  the terminal does not seem to be doing anything, I just get a cursor. And when I stop gdm, pretty much the same thing, I get a black screen but the option to log back in never shows up, there is just a cursor there. I have absolutely no idea why this is happening. Someone please help. Thanks in advance.

---

