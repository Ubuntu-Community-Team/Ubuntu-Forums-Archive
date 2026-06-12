---
title: "Problems with bumblebee on 16.04 (Intel + GT850M)"
date: 2017-09-27
forum: Hardware
---

### Post by silex89 on 2017-09-27
Dear all: I installed Ubuntu on my HP Laptop and runs like a charm except for one thing: The NVidia card. The setup I have is the following:

```
$ lspci -k | grep -A 2 -E "(VGA|3D)"
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
    Subsystem: Hewlett-Packard Company 4th Gen Core Processor Integrated Graphics Controller
    Kernel driver in use: i915
--
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 850M] (rev a2)
    Subsystem: Hewlett-Packard Company GM107M [GeForce GTX 850M]
    Kernel driver in use: nvidia
```

I have followed a lot of different guides on how to make Bumblebee working for Ubuntu 16.04 and I have had no success so far. After I try to use optirun or primus run I get error outputs.
```

$ optirun glxgears
[11706.238233] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) 
[11706.238264] [ERROR]Aborting because fallback start is disabled.

$ primusrun glxgears
primus: fatal: Bumblebee daemon reported: error: [XORG] (EE)
```

Here is the output of systemd

```
$ systemctl status bumblebeed
&#9679; bumblebeed.service - Bumblebee C Daemon
   Loaded: loaded (/lib/systemd/system/bumblebeed.service; disabled; vendor pres
   Active: active (running) since mié 2017-09-27 12:06:05 CLST; 4s ago
 Main PID: 22075 (bumblebeed)
   CGroup: /system.slice/bumblebeed.service
           &#9492;&#9472;22075 /usr/sbin/bumblebeed

sep 27 12:06:05 Hagith systemd[1]: Started Bumblebee C Daemon.
sep 27 12:06:05 Hagith bumblebeed[22075]: [11691.847483] [INFO]/usr/sbin/bumbleb

```

Please let me know what could be wrong.

Thank you in advance

---

### Post by efflandt on 2017-09-28
I have not used bumblebee since Ubuntu 13.10 when there was no other choice. At that time optirun worked, but I never could get primusrun to work for anything. And it was a pain using optirun for Steam games, because you had to add extra game launch options for it to work. At that time the Intel driver was slower too, TF2 using the Intel driver on a system with bumblebee was very low frame rate and audio would loop. In Ubuntu 14.04 using nvidia-prime even when switched to Intel graphics, TF2 would smoothly play at about 30 fps (or much faster using Nvidia graphics). I had an i7 laptop with Intel HD 4600 and Nvidia GTX 765M graphics.

Since Ubuntu 14.04 the nvidia driver packages include nvidia-prime. You should be able to select which graphics to use from the last page of "NVIDIA X Server Settings", although, you might need to log out of X and back in after switching Nvidia to Intel, or might need to reboot going Intel to Nvidia. With nvidia-prime no game launch options are required. It has been awhile because my gaming laptop no longer turns on properly, but I would definitely choose nvidia-prime rather than bumblebee.

---

### Post by silex89 on 2017-09-28
> **efflandt said:**
> I have not used bumblebee since Ubuntu 13.10 when there was no other choice. At that time optirun worked, but I never could get primusrun to work for anything. And it was a pain using optirun for Steam games, because you had to add extra game launch options for it to work. At that time the Intel driver was slower too, TF2 using the Intel driver on a system with bumblebee was very low frame rate and audio would loop. In Ubuntu 14.04 using nvidia-prime even when switched to Intel graphics, TF2 would smoothly play at about 30 fps (or much faster using Nvidia graphics). I had an i7 laptop with Intel HD 4600 and Nvidia GTX 765M graphics.

Since Ubuntu 14.04 the nvidia driver packages include nvidia-prime. You should be able to select which graphics to use from the last page of "NVIDIA X Server Settings", although, you might need to log out of X and back in after switching Nvidia to Intel, or might need to reboot going Intel to Nvidia. With nvidia-prime no game launch options are required. It has been awhile because my gaming laptop no longer turns on properly, but I would definitely choose nvidia-prime rather than bumblebee.

Well, I was hoping to avoid using PRIME because I use my discrete card quite often and I want to precisely avoid loging in/out to switch cards. I come from Arch Linux and they make it easier to use Bumblebee. I remember performing only two or three steps in order to get it working and Ubuntu made it more difficult. I find that a little bit surprising actually.

So, any advises on what to do in this regard?

---

