---
title: "Newest NVIDIA driver renders desktop unusable UBUNTU 14.04"
date: 2015-11-04
forum: Hardware
---

### Post by tiger8 on 2015-11-04
I have an NVIDIA GTX 750ti, which was previously stable using the 344(I think) driver. However, it made my wireless slow, and one of my keyboards stopped working properly. 
So I decided to upgrade to the lates NVIDIA drivers, 352.55. While installing, it said a startup script had failed, but I opted to continue. Everything proceeded normally from there.

But when I rebooted, my computer never hit the splash screen, and instead displayed a flashing red underscore in the top left corner of my first monitor. 
I restarted the computer and booted to recovery mode. It took me to a command line login screen, but before I had entered my password, the screen went blank. Hitting the power button yielded the usual shutdown messages and it shutdown without a problem. 
So I tried booting regularly again, and it made it to the splash screen, and then to a command line login, but once again went blank. Pressing the power button had the same behavior. 

I'm currently trying to boot into graphics failsafe mode.

So my first question is; Does anyone have any idea how to resolve this? I don't mind dropping back to the previous drivers, they worked well enough.
Second question; How long should booting into failsafe mode take? It's been siting on the line ```
/dev/sdb1: clean, 344576/7331840 files, 15110143/29304832 blocks
``` for about ten minutes now.

---

### Post by efflandt on 2015-11-05
How are you installing drivers, Ubuntu packages (recommended) or scripts from nvidia.com. The current recommended way to get nvidia driver packages newer than in the normal repositories is graphics-drivers/ppa [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

I have been using **nvidia-352** package (352.55) for awhile now with a GTX 750 Ti in 64-bit 14.04, the ppa also has **nvidia-355** (355.11) and **nvidia-358** (358.09) packages.```
efflandt@XPS-8100-1404:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-352                                            352.55-0ubuntu0~gpu14.04.2                          amd64        NVIDIA binary driver - version 352.55
ii  nvidia-opencl-icd-352                                 352.55-0ubuntu0~gpu14.04.2                          amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       358.09-0ubuntu0~gpu14.04.1                          amd64        Tool for configuring the NVIDIA graphics driver
```

If you used the nvidia.com script, I think that script has some way to remove drivers, but I have never used those so have no details.

Note that since the default nouveau driver in 14.04.1 did not support the new Maxwell chip (and neither did nvidia-current package), I booted a recovery kernel, enabled networking from the text dialog (wait until it returns to menu if you get any errors about unrecognised hardware), then selected root console from menu. From there you can uninstall/install packages without even having to use sudo.

---

### Post by tiger8 on 2015-11-05
Thanks for the reply.
I installed using the script from the NVIDIA site. I didn't realize i could install the drivers using the package manager.
I'll try booting to root when I get home. Hopefully that will work.

---

### Post by tiger8 on 2015-11-06
Well I booted to recovery mode and tried to enable networking. It got stuck right where it did when I tried to enter graphics failsafe mode. I left it overnight, and no progress. If anyone has any other ideas, I'm all ears. If not, I'm just going to reinstall this afternoon.

---

### Post by pqwoerituytrueiwoq on 2015-11-07
Run the nvidia uninstaller
i think it is called nvidia-uninstaller
but just to be sure
```
ls /usr/bin | awk '/nvidia/ && /install/'
```
remove /etc/X11/xorg.conf
make sure nouveau is not blacklisted
```
cat /etc/modprobe.d/*|awk '/blacklist/ && /nouveau/'
```
if it finds that it is remove that line from what ever file has it

that should get you back to the stock opensource driver

---

### Post by tokyobadger on 2015-11-08
> **tiger8 said:**
> I have an NVIDIA GTX 750ti, which was previously stable using the 344(I think) driver. However, it made my wireless slow, and one of my keyboards stopped working properly. 
So I decided to upgrade to the lates NVIDIA drivers, 352.55. While installing, it said a startup script had failed, but I opted to continue. Everything proceeded normally from there.

But when I rebooted, my computer never hit the splash screen, and instead displayed a flashing red underscore in the top left corner of my first monitor. 
I restarted the computer and booted to recovery mode. It took me to a command line login screen, but before I had entered my password, the screen went blank. Hitting the power button yielded the usual shutdown messages and it shutdown without a problem. 
So I tried booting regularly again, and it made it to the splash screen, and then to a command line login, but once again went blank. Pressing the power button had the same behavior. 

I'm currently trying to boot into graphics failsafe mode.

So my first question is; Does anyone have any idea how to resolve this? I don't mind dropping back to the previous drivers, they worked well enough.
Second question; How long should booting into failsafe mode take? It's been siting on the line ```
/dev/sdb1: clean, [344576/7331840]("tel:344576/7331840") files, [15110143/29304832]("tel:15110143/29304832") blocks
``` for about ten minutes now.
1. Your card was "previously stable" with nvidia 34x (no 344 AFAIK) - how would you describe the transition from stable to unstable?

2. What evidence do you have that the nvidia 34x driver affected your wifi connection? 

3. How many keyboards are you using? The one that stopped working properly - hardware details and failure description

4. Nvidia driver update - already covered

5. Never hit the splash screen: what method do you use to get Plymouth to play nice with the nvidia proprietary drivers?

6. Top left corner of your first monitor: same as #3 above

---

