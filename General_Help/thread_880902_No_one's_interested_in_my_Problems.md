---
title: "No one's interested in my Problems"
date: 2008-08-05
forum: General Help
---

### Post by nnjond on 2008-08-05
Hi, 
I've always received a lot of help and advice in the past, but no one's is taking an interest in my most recent posts. Am I doing something wrong ?

[http://ubuntuforums.org/showthread.php?p=5526952#post5526952](http://ubuntuforums.org/showthread.php?p=5526952#post5526952)

[http://ubuntuforums.org/showthread.php?p=5526971#post5526971](http://ubuntuforums.org/showthread.php?p=5526971#post5526971)

---

### Post by blazercist on 2008-08-05
first thing is u should usually wait 24 hours before expecting a reply or trying again, also you shoulndt cross post like this especially within 24 hours.

you need to give information about your hardware /drivers version of ubuntu 32/64 bit? kernel

```
uname -r
```
```
lspci
```

---

### Post by LowSky on 2008-08-05
I bet it has nothing to do with your perosnality, most likely no on knows how to answer your question, or its been posted so many countless times all you had to do is search or use google.
So to help...
First off what kind of hardware? Second why make a new post instead of bumpping the other threads? Third What exactly are you trying to do?

---

### Post by overdrank on 2008-08-05
HI and on your first link I was going to reply but it would help to have a little info like graphics card and you could search.
The second link I have no clue. :)
It has nothing to do with you, its because I just do not know.

---

### Post by overdrank on 2008-08-05
> **LowSky said:**
>  Second why make a new post instead of bumpping the other threads? Third What exactly are you trying to do?

Good point and I will close the other threads as now the issues are being addressed here.

---

### Post by nnjond on 2008-08-05
Thanks for your interest. As i understandit:

nick@nick-desktop:~$ uname -r
2.6.24-19-generic
nick@nick-desktop:~$ -r
bash: -r: command not found
nick@nick-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
nick@nick-desktop:~$ 



Prob# 1
 Secondary scrn options
Hi, My Secondary screen options are unavailable. Can I alter this?

Prob # 2

I would like my Capture to be Line-in L+R, but for some reason R is given over to mic. How can I change this?

Thanks.

---

### Post by blazercist on 2008-08-05
Well ok apparently you are using hardy with the latest kernel, but it appears that your graphics card is SiS, not intel/ati/nvidia im not sure about the driver support for that card let alone dual monitor support and I have no experience with that chipset.

as far as capture for line in I assume you are using pulse audio which makes me useless.  In the event you are using alsa you may want to try 

```
alsamixer
```
and try adjusting the settings.

---

### Post by overdrank on 2008-08-05
> **nnjond said:**
> Thanks for your interest. As i understandit:
```

nick@nick-desktop:~$ uname -r
2.6.24-19-generic
nick@nick-desktop:~$ -r
bash: -r: command not found
nick@nick-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
nick@nick-desktop:~$ 
```



Prob# 1
 Secondary scrn options
Hi, My Secondary screen options are unavailable. Can I alter this?

Prob # 2

I would like my Capture to be Line-in L+R, but for some reason R is given over to mic. How can I change this?

Thanks.

On the [SiS] 661/741/760, they are not supported well. You can try and change the driver in ```
gksu displayconfig-gtk
``` there you can try and change the driver and maybe find a solution.

---

### Post by nnjond on 2008-08-05
Sorry, I've missunderstood the problem. I do not want a second scrn, but another option to extend my default scrn is ghosted, Can I alter this?

---

