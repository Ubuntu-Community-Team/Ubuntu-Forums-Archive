---
title: "Nvidia Optimus does not work on Alienware 13 R3"
date: 2017-10-06
forum: Hardware
---

### Post by Voc on 2017-10-06
Hello everyone,

I have an alienware 13 r3 that I've been trying to get the nvidia optimus to work on.  I installed nvidia-prime and the latest nvidia driver from the repositories, and when I run the command ```
sudo prime-select query
``` I get ```
nvidia
```, so the driver seems to be recognized and working.  However, when trying to run an application that uses glx I will get an error.  When I run glxgears I get ```
Error: couldn't get an RGB, Double-buffered visual

```, and trying to start steam gives an error "OpenGL GLX extension not supported by display".  I never had bumblebee installed (it's a fresh install) so I'm not sure where the problem is coming from.  Any ideas?

Thanks!
Luke

---

### Post by efflandt on 2017-10-06
What do you get for the following:```
glxinfo | grep -E 'direct render|OpenGL'
lspci | grep -E 'VGA|3D'
```

---

### Post by Voc on 2017-10-07
For the first one I get:
```
:~$ glxinfo | grep -E 'direct render|OpenGL'
Error: couldn't find RGB GLX visual or fbconfig
```
and the second one:
```
:~$ lspci | grep -E 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1c20 (rev a1)
```

---

### Post by efflandt on 2017-10-07
Which Ubuntu or related Linux distro version are you running? And do you know what Nvidia graphics chip it has?

Normally lspci would identify your Nvidia chip. My gaming laptop with Intel HD 4600 graphics and Nvidia GTX 765M no longer turns on properly, so I cannot demonstrate that. But its GTX 765M was shown as 3D instead of VGA in lspci and usually that also identifies the Nvidia chip. For example on my desktop PC:

01:00.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 3GB] (rev a1)

It looks like your Nvidia graphics is [1c20]("https://pci-ids.ucw.cz/read/PC/10de/1c20") GP106M [GeForce GTX 1060 Mobile 3GB] and it is possible that the default nouveau driver or older nvidia drivers do not support that. If you need to add newer nvidia drivers, you can add the graphics-drivers ppa:```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-384
```Note that Ubuntu 16.04 or newer can use **apt** instead of **apt-get**. The most recent Nvidia driver is actually nvidia-387. I am actually currently using nvidia-381 for my desktop GTX 1060, but my Ubuntu 16.10 is no longer supported, so this weekend I need to see if the long term support version Ubuntu 16.04.3 LTS works for me now or update to shorter term 17.04.

---

### Post by Voc on 2017-10-12
Sorry for the long response.

I am using a core Lubuntu built from a base installation of Ubuntu server 16.04.  I think the problem may have been that I didn't have a required software package manually installed because when I installed lubuntu-core it installed an additional couple of packages, after which everything started working.  I am able to play games in steam and run glxgears.

Thanks!
Luke

---

