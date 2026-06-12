---
title: "Unstable behaviour - Can't install nvidia-96"
date: 2011-05-11
forum: Hardware
---

### Post by danielsender on 2011-05-11
Hi,

I just upgraded my [SIZE=1]Dell Precision M50 with the NVIDIA Quadro4 500 Go grafic sub-system. The main problem is that often it freezes and nothing responds. After a couple of minutes it comes back to life. It is random and it appears to depend on what applications I have running, although I still could not identify them. I though that perhaps was due to the experimental graphic drive so I attempted to load to proprietary nvida-96 driver. But in synaptic it says that the package is broken. When I click on "fix broken packages" the response is "successful", however when I re-attempt to install it comes back with the same message. If I attempt to do it from the terminal I get the following dialog:

[/SIZE]```

[SIZE=1]sudo apt-get install nvidia-96
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-96 : Depends: xorg-video-abi-8.0 but it is not installable
             Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but it is not going to be installed
E: Broken packages[/SIZE]

```One more thing: if in synaptic I attempt to do a complete removal of nvidia-96 the "Apply" button stays grayed in.

Thanks.

Daniel

---

### Post by lnebrown on 2011-05-17
I'm having the exact same problem.  Any advice would be appreciated!

---

### Post by MoebusNet on 2011-05-20
The error message you get about xorg is because after Ubuntu 8.04, the xorg version does not support the older 96, 73 and other drivers. You can look up the release notes for Ubuntu 8.10 for full details. You might try the legacy driver from Software Center, or from NVIDIA website. Best of luck!

---

### Post by danielsender on 2011-05-27
When I was running 10.10 I could install 96 and it was running fine. Now I can't even install with the nvidia file NVIDIA-Linux-x86-96.43.19-pkg1.run. I guess that something changed from 10.10 to 11.04.

---

### Post by cascade9 on 2011-05-29
> **MoebusNet said:**
> The error message you get about xorg is because after Ubuntu 8.04, the xorg version does not support the older 96, 73 and other drivers. You can look up the release notes for Ubuntu 8.10 for full details. You might try the legacy driver from Software Center, or from NVIDIA website. Best of luck!

8.04 might be the last version that works with the 71.XX drivers (not 73.XX), but the 96.XX drivers were working up till 10.10.  

You may never be able to run the 96.XX drivers with 11.04, if nVidia dont make 96.XX drivers that support the xorg version used. 

Theres been a few  'bumps' here and there with ubuntu and the 96.XX drivers. Mainly because ubuntu tends to use the newest version of xrog possible.  When the nvidia drivers dont support the version of xorg in whatever version of ubuntu, you have to wait until the drivers with support come out. Since the 96.XX drivers are for fairly old cards, its low on nVidias priority list....

---

