---
title: "NVIDIA Developer Drivers Install"
date: 2011-01-06
forum: Hardware
---

### Post by chwebb1 on 2011-01-06
Hello All,
I am trying to install the NVIDIA developer drivers on Ubuntu 10.04 on a Lenovo ThinkPad W510 with NVIDIA Quadro FX 880M. I downloaded the drivers from [http://developer.nvidia.com/object/cuda_3_2_downloads.html](http://developer.nvidia.com/object/cuda_3_2_downloads.html). I have tried to follow the directions from [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074), [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074) and [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual). I am currently getting an error saying that Nouveau is in use, and I can't install the driver because of that, despite being uninstalled and blacklisted. Does anyone have any idea on how to install these? Thanks!

---

### Post by BicyclerBoy on 2011-01-06
If the xorg log file has the nouveau loaded info then your blacklisting has not worked.....
Double check...

[http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/commonproblems.html](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/commonproblems.html)

section 8.1

You can un-install the nouveau driver in synaptic BUT the kernel module remains.
That what blacklisting deals to..

Get your kernel headers  uname -r etc etc
Get your nvidia driver from 

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

it's easier...

---

### Post by chwebb1 on 2011-01-06
That Nvidia web site doesn't say how to reconfigure Xorg in that tutorial, and a quick Google search leads to nothing promising. How do I make sure Xorg doesn't launch Nouveau?

Also, are the developer drivers the same as the standard drivers? I was under the impression that they were different. 

Thanks for your help.

---

### Post by efflandt on 2011-01-06
Just curious which version drivers you downloaded from nvidia?

It is usually much easier to install nvidia drivers from the repositories, which automatically takes care of moving nouveau out of the way and auto updating the modules during kernel updates.

If you need a newer version than the repos normally offer, you can add the x-swat ppa, which currently has nvidia 260.19.29 for Lucid (10.04) or Maverick (10.10).  [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

If you put everything back to normal, adding that is simply a matter of:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```Then go to System > Administration > Hardware Drivers (or Additional Drivers in Maverick), "activate" nvidia, and reboot.  Or if you had earlier Ubuntu nvidia drivers after adding the repository above, from Hardware Drivers "remove" nvidia, reboot, then "activate" nvidia, and reboot

---

### Post by chwebb1 on 2011-01-06
I downloaded Developer edition 260.19.26, for use with CUDA. I understand how to set up a PPA, but I wasn't aware that you could simply download the standard NVIDIA drivers for use with CUDA.

---

### Post by chwebb1 on 2011-01-08
For anyone else having this issue, I simply installed the regular drivers after following all of the steps above, and then installed the developer drivers.

---

