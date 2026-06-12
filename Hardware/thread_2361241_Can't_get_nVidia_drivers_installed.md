---
title: "Can't get nVidia drivers installed"
date: 2017-05-14
forum: Hardware
---

### Post by wintermute115 on 2017-05-14
I have a new laptop with a clean install of Kubuntu 17.04, and I can't get the nvidia drivers installed properly. When I try to install nvidia-375 from the distro packages, or nvidia-381 from the graphics-drivers PPA, I can't open any new windows (Konsole, file browser, etc) until I uninstall it and go back to the nouveau driver.

I will say I've not tried rebooting after installing the new drivers, as I'm concerned about not being able to log in if it doesn't work.

Can anyone help?

```
$ sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
model    : GP106M [GeForce GTX 1060]
modalias : pci:v000010DEd00001C60sv00001558sd00007505bc03sc00i00
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-375 - distro non-free recommended

```

---

### Post by Bashing-om on 2017-05-14
wintermute115; Hello;

Concurrence on the 375 version :
 [http://www.nvidia.com/download/driverResults.aspx/118290/en-us](http://www.nvidia.com/download/driverResults.aspx/118290/en-us)

At this time make sure there is no installed drivers conflict:
```

dpkg -l | grep -i nvidia

```
if all that is installed (ii) are the 375 versioning packages, then yes reboot to see the effect.
> 
sysop@x1604:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                               0.8-3ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-375                                375.66-0ubuntu0~gpu16.04.1                    amd64        NVIDIA CUDA runtime library
ii  nvidia-375                                  375.66-0ubuntu0~gpu16.04.1                    amd64        NVIDIA binary driver - version 375.66
ii  nvidia-opencl-icd-375                       375.66-0ubuntu0~gpu16.04.1                    amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                         amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             381.22-0ubuntu0~gpu16.04.1                    amd64        Tool for configuring the NVIDIA graphics driver
sysop@x1604:~$ 


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by efflandt on 2017-05-16
New graphics drivers are not going to work "until after" you reboot. So maybe not rebooting after install "is" your problem.

I am assume that since it is a laptop that you have hybrid Intel and Nvidia graphics. The system will likely boot using the Intel graphics until you change that to Nvidia using "NVIDIA X Server Settings". My laptop with hybrid graphics will not turn on, so not sure if it is still that way, but if I switched from Nvidia to Intel graphics all I had to do was log out of X and log back in. But if I switched from Intel to Nvidia graphics, I had to reboot.

---

