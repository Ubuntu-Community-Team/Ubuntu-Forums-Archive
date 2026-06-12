---
title: "Dell E1505 X1400 and Intel 3495 wireless"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by bsgjunkie on 2007-01-01
I'm a linux newbie, but feel comfortable with most of the guides I've seen. I installed 6.10 yesterday. I tried using the live CD, but received the 'no root' bug in the partition manager and downloaded the alternative CD instead. I installed the alternative cd last night without any problem during install. I noticed after install that my wifi wasn't detected, although it was with the livecd. I also tried to set up the graphics drivers, yet it wasn't successful. I think I've found the problem with the graphics card, just dont' know how to fix it.

Its a Dell E1505 core 2 duo, with an ati x1400 graphics card. I used the guide found here at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) to install the repositories. I followed the steps, and at the end it has you verfiy the install by using the command 'fglrxinfo' - It returns the info found below instead of the ATI info as suggested in the guide.

$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I followed the trouble shooting section and it seems the below is my problem -

Make sure that the resctricted-modules package installed correspond to the kernel your are running and that you can load the fglrx driver, either by issuing the command "sudo modprobe fglrx" or by verifying that the module appears in the list of loaded modules, by issuing the command "lsmod";

When I run sudo modprobe fglrx it returns - FATAL: Error running install command for fglrx
And fglrx isn't found in the load mods list either.

The guide doesn't mention what I can do to fix this. Any help would be appreciated.

I have no idea where to start with the wifi card. Like I said, I'm a complete newbie. With the livecd the Wifi card was listed under system>administartion>networking - its not there with the install. Its a intel 3495 wireless card and is supposed to be supported out of the box.

Any help would be appreciated
Junkie

---

### Post by bsgjunkie on 2007-01-04
Ok, I was a little wrong about the wifi. The device manager shows the intel wireless care, but the network app doesn't. I'm sure this is an easy fix - A hint would nice.

---

