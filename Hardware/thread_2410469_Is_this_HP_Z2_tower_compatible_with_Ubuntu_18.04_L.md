---
title: "Is this HP Z2 tower compatible with Ubuntu 18.04 LTS?"
date: 2019-01-16
forum: Hardware
---

### Post by kenrichardson on 2019-01-16
Hello folks

I'm looking at purchasing the above machine with the intention of dual booting with windows 10.

It would be configured with 2 HDs, an intel core i7-8700K CPU, and  an NVIDIA Quadro P620 GPU.

Has anyone had experience with this configuration, or something similar (e.g., an HP Z240 tower), or otherwise has a view on Ubuntu compatibility? I note that Ubuntu have added support for the NVIDIA Quadro P620 GPU to their NVIDIA driver ([http://tipsonubuntu.com/2018/01/31/install-nvidia-390-25-ubuntu-17-10-18-04/](http://tipsonubuntu.com/2018/01/31/install-nvidia-390-25-ubuntu-17-10-18-04/)),  so presumably that should be OK.

Regards  Ken

---

### Post by drlamb on 2019-01-16
I've been utilizing a combination of Z240/30/23's for an Ubuntu 18.04 project at work and have had no issues installing Ubuntu or the nvidia drivers (via ubuntu-drivers autoinstall). K620s, P600s, you name it. You shouldn't have an issue, and if you do it'll likely be to nouveau incorrectly modesetting the GPU. If you cannot boot the live disk (assuming Ubuntu desktop) due to graphical freezes try booting with nouveau.modeset=0 as a kernel parameter.

---

### Post by kenrichardson on 2019-01-16
OK, thanks. Very helpful. Ken

---

### Post by smittles on 2019-09-05
For what it's worth, I've been running 18.04 desktop edition on a Z240 SFF, and there are a few issues that I cannot seem to get a handle on. 

First, when the OS was Windows, I was able to connect via wi-fi, but now I am unable to. 

Second, and this is the more annoying of the issues, the fans run *constantly*. Sure, the machine stays nice and cool, but none of the forums I've visited have been able to answer why my fans don't shut off.

---

### Post by sevendogs1337 on 2019-09-05
Ran Ubuntu on my z800 with no issues using an Nvidia GTX 1050ti. No wifi on the 800, only dual nics. It's loud as well, but that's not Ubuntu's fault...

---

