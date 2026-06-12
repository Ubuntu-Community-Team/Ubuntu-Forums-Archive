---
title: "8600GTS 6-pin connector"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by psycho5 on 2007-11-10
I made a successful fresh install using the **Alternate CD 7.10 Ubuntu for Amd 64**..

I am running **Nvidia8600GTS**

I've followed **[http://www.ubuntugeek.com/how-to-fix...acy-users.html](http://www.ubuntugeek.com/how-to-fix...acy-users.html)** which shows how to disable restricted drivers and then download the nvidia drivers from its website and install them...

after installation of the official drivers , i restart xorg
[B]
sudo /etc/init.d/gdm start[/B]

however when i boot up with those drivers successfully installed, it boots into safe graphics mode, really messed up, where half the window is on the left side of my screen and half on my right. 

I tried using the normal restricted drivers **apt-get install nvidia-glx-new** but still I get the still result, booting into safe graphics mode. 

I've followed the official Howtobinarydrivers for Nvdia guide and still I get safe graphics mode. 

I want to ask could it be because my video card isn't connected by the 6-pin direct power supply connection for Pci-ex cards? That connection provides extra power from the Power supply directly to the card. :confused:

That's the only thing I can think of that could be stopping Ubuntu from booting normally.

If anyone has been successful in installing Ubuntu 7.10 with 8600GTS please let me know how you did it. 

Thanks alot

---

### Post by Mondoman on 2007-11-10
You certainly do need to have that 6-pin plug connected.

---

