---
title: "Solution for NVIDIA not recognized"
date: 2009-04-26
forum: Hardware
---

### Post by jazzroy on 2009-04-26
hi,
like many others 9.04 didn't put any NVIDIA drivers on my Restricted hardware panel and also in Synaptic.
It seems that some mobile chips aren't listed as compatible although they are.

Here is the solution that worked for me:

1- enable all restricted/universe/multiverse repos (just to be sure, you should always do it)

2- download the NVIDIA 180 drivers in your home folder:

For 32 bit: 

[http://us.download.nvidia.com/XFree86/Linux-x86/180.29/NVIDIA-Linux-x86-180.29-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/180.29/NVIDIA-Linux-x86-180.29-pkg1.run)

For 64 bit:

[http://us.download.nvidia.com/XFree86/Linux-x86_64/180.29/NVIDIA-Linux-x86_64-180.29-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/180.29/NVIDIA-Linux-x86_64-180.29-pkg2.run)

3- open a terminal and type:

```
sudo apt-get install build-essential linux-headers-$(uname -r) xserver-xorg-dev

```

4- copy the following commands on a paper and exit X by doing:

CTRL-F2 (or F3 or another one you like)

5- you'll be in a shell environment, login and then type:

```
sudo killall gdm
```

this will end your X session

6- type:

```
sudo sh NVIDIA-Linux-x86_64-180.29-pkg2.run
```

Note: you have to put the name of the package you downloaded!!

7- Follow the instructions and let the installation manager do all the steps, including the rconfiguration of your X server.

8- When finished type:

```
startx
```

and voilà, you'll be again in X using your nvidia driver.
now you can fire your delighting advanced desktop effects or play games, or even better run your lovely Blender.

9- to get more control over your videocard install from Add/Remove the Nvidia X server settins

10- Smile!

---

