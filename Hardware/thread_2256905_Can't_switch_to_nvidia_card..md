---
title: "Can't switch to nvidia card."
date: 2014-12-15
forum: Hardware
---

### Post by daniel229 on 2014-12-15
Hi, i recently installed nvidia drivers because of steam, i installed them by the 2 codes below, and by selecting the nvidia drivers from the adicional drivers menu, after that i restarted the pc. when logged back in and by going to nvidia X server settings, i cannot switch to nvidia card.
[COLOR=#000000]
Software: Ubuntu 14.10
Hardware: NVIDIA gt740m

Code i used to install drivers.
```
  [/COLOR][COLOR=#000000]sudo apt-get install bumblebe[/COLOR][COLOR=#000000]  
```
[/COLOR][COLOR=#000000]```
 [/COLOR][COLOR=#000000]sudo apt-get install nvida-curent [/COLOR][COLOR=#000000]
```[/COLOR][COLOR=#000000]

[/COLOR][IMG][[IMG]http://s16.postimg.org/rlxjpnynl/Captura_de_ecr_de_2014_12_15_20_24_38.jpg[/IMG]]("http://postimg.org/image/rlxjpnynl/")[/IMG]

---

### Post by oldfred on 2014-12-15
It looks like you need a newer version than in repository.
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
When you do a search it shows the oldest as 337.xx

So you may need a ppa for the complied nVidia drivers that are newer.

Several ppa, not sure which may be better.
       PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
[https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed)
Kernel updater script - also git methods
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)

---

### Post by grahammechanical on 2014-12-16
Why did you install Bumblebee? That is an open source video driver for Hybrid graphics using Nvidia optimus technology. Do you have hybrid graphics?

I have no experience of hybrid graphics myself. Best I can offer

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

That third link shows you what the Nvidia Xserver Settings manager should be offering you if you have Optimus technology. It includes Prime Profiles, which is where we switch from Intel to Nvidia. The image you show does not include that.

Regards.

---

### Post by daniel229 on 2014-12-16
Hey!, first of all, thanks for you responses, i did followed a guide to update my driver, all good, until i restarted the pc... Ubuntu woulnd't load, only a pitch black screen, after that i reinstaled ubuntu and keeped the 331 drivers, now it's all good, thx!

[COLOR=#000000]"Install Nvidia 340.24 from ppa[/COLOR]:mad:[COLOR=#000000]org-edgers/ppa"[/COLOR]
[LINK] [http://www.sysads.co.uk/2014/07/inst...-ubuntu-14-04/]("http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/") [/LINK]

---

