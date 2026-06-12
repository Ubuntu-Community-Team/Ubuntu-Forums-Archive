---
title: "Nvidia graphics driver"
date: 2011-07-19
forum: Hardware
---

### Post by freeallforever on 2011-07-19
Okay, I have the activated but not in use problem with the proprietary nvidia driver.
I have tried reinstalling xorg file, twice, both times I had to reinstall ubuntu once I restarted because the laptop would not start. I have deleted the nouveau driver through terminal, no help. I have tried reinstalling the properietary driver countless times. Searching for the answers gives me outdated info for 9.04 versions and before that have functons the current ubuntu doesn't seem to have. 

I am comfortable using terminal if that is better to solve the issue, but have no general knowledge of programming or even the linux commands. 

I would like to use linux AND get the graphics working on this laptop! 
Please help, thank you.   
:guitar:

---

### Post by Shrobby7x on 2011-07-20
It would seem like this is a problem for a lot of users... I'm in the same boat. 
freeallforever, just tell me if I did exactly what you did, maybe there is some overlap that we can agree on that just might solve our issue.

I've download the FreeBSD edition of the Nvidia drivers and installed them as correctly as I can assume. When I try to run the "NVIDIA X Server Settings" from System>Administration I get the error:

```

You do not appear to be using the NVIDIA X driver.
Please edit your X configuration file (just run 'nvidia-
xconfig' as root), and restart the X server.

```When I run the 'nvidia-xconfig' as root (su), I verify that it wrote it correctly (gedit /etc/X11/xorg.conf) and it seems like it did as far as I can understand it. Then, I restart or log off (I've tried both), only to get a black screen with no picture. If I restart enough times, I'll gain access to the recovery mode and I'll re-write (to blank) the xorg.conf file and I'm back to square one.

I've purged the nouveau drivers as suggested by other websites as help for previous versions of Ubuntu.

A peculiarity that I have found however... 
When I first decided to install Ubuntu, I tried it as a dual boot with Windows 7 Ultimate x64 as the primary OS. I installed Ubuntu just fine, and all seemed dandy as Unity was activated and worked just fine. The problem wasn't the nVidia drivers as I didn't get far enough to use them, but my screens resolution wouldn't fit the entirety of the desktop at any resolution. The fix was not to dual boot, but to run as a VM. Now, I have VMWare Player running Ubuntu inside of Win7 and it works fine, but Unity is not enabled because I do not have the hardware requirements to run it (EVGA GTX 570 on an i7 w/ 6GB RAM ain't enough?! guess not...). My thoughts were to install the nVidia drivers to resolve the issue, but it hasn't worked.

If you have anymore input, or if you figured it out, let me know!

---

### Post by freeallforever on 2011-07-20
> **Shrobby7x said:**
> It would seem like this is a problem for a lot of users... I'm in the same boat. 
freeallforever, just tell me if I did exactly what you did, maybe there is some overlap that we can agree on that just might solve our issue.

I've download the FreeBSD edition of the Nvidia drivers and installed them as correctly as I can assume. When I try to run the "NVIDIA X Server Settings" from System>Administration I get the error:

```

You do not appear to be using the NVIDIA X driver.
Please edit your X configuration file (just run 'nvidia-
xconfig' as root), and restart the X server.

```When I run the 'nvidia-xconfig' as root (su), I verify that it wrote it correctly (gedit /etc/X11/xorg.conf) and it seems like it did as far as I can understand it. Then, I restart or log off (I've tried both), only to get a black screen with no picture. If I restart enough times, I'll gain access to the recovery mode and I'll re-write (to blank) the xorg.conf file and I'm back to square one.

I've purged the nouveau drivers as suggested by other websites as help for previous versions of Ubuntu.

A peculiarity that I have found however... 
When I first decided to install Ubuntu, I tried it as a dual boot with Windows 7 Ultimate x64 as the primary OS. I installed Ubuntu just fine, and all seemed dandy as Unity was activated and worked just fine. The problem wasn't the nVidia drivers as I didn't get far enough to use them, but my screens resolution wouldn't fit the entirety of the desktop at any resolution. The fix was not to dual boot, but to run as a VM. Now, I have VMWare Player running Ubuntu inside of Win7 and it works fine, but Unity is not enabled because I do not have the hardware requirements to run it (EVGA GTX 570 on an i7 w/ 6GB RAM ain't enough?! guess not...). My thoughts were to install the nVidia drivers to resolve the issue, but it hasn't worked.

If you have anymore input, or if you figured it out, let me know!
I have done the things you have except the windows stuff. I am not aware of the rewrite of the recovery mode xorg file, might need to learn that instead of reinstalling the OS.

---

### Post by jocko on 2011-07-20
> **freeallforever said:**
> Okay, I have the activated but not in use problem with the proprietary nvidia driver.
I have tried reinstalling xorg file, twice, both times I had to reinstall ubuntu once I restarted because the laptop would not start. I have deleted the nouveau driver through terminal, no help. I have tried reinstalling the properietary driver countless times. Searching for the answers gives me outdated info for 9.04 versions and before that have functons the current ubuntu doesn't seem to have. 

I am comfortable using terminal if that is better to solve the issue, but have no general knowledge of programming or even the linux commands. 

I would like to use linux AND get the graphics working on this laptop! 
Please help, thank you.   
:guitar:
What reason do you have to think that the driver is not in use? Only the message from jockey (the hardware driver manager)?
The "activated but not in use problem" is not a real problem, it's just a bug in jockey that makes it report that the driver is not in use even if it is.
I (and probably everyone else with an nvidia card that use natty and have installed the nvidia driver) get the same message from jockey, but nevertheless, the driver is in use.
If your only reason is that silly message from jockey, just ignore it. 

To check which driver your card actually uses:
```
lspci -k
```
Find your graphichs card in the output. I get:
```
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)
    Subsystem: Giga-byte Technology Device 34cb
    [COLOR=Blue]**Kernel driver in use: nvidia**[/COLOR]
    Kernel modules: nvidia-current, nouveau, nvidiafb
```

---

### Post by freeallforever on 2011-07-20
> **jocko said:**
> What reason do you have to think that the driver is not in use? Only the message from jockey (the hardware driver manager)?
The "activated but not in use problem" is not a real problem, it's just a bug in jockey that makes it report that the driver is not in use even if it is.
I (and probably everyone else with an nvidia card that use natty and have installed the nvidia driver) get the same message from jockey, but nevertheless, the driver is in use.
If your only reason is that silly message from jockey, just ignore it. 

To check which driver your card actually uses:
```
lspci -k
```Find your graphichs card in the output. I get:
```
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)
    Subsystem: Giga-byte Technology Device 34cb
    [COLOR=Blue]**Kernel driver in use: nvidia**[/COLOR]
    Kernel modules: nvidia-current, nouveau, nvidiafb
```
```
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
    Subsystem: CLEVO/KAPOK Computer Device 5140
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

``` I get this, I know it doesn't work properly because when I uninstall it and let the experimental driver be used some old games work, unfortunately it is not good enough for newer games with 3d support and higher effects. I also get downgraded to the really old version of ubuntu desktop and can't use the unity (not that I want to cause it sucks).

---

### Post by jocko on 2011-07-20
> **freeallforever said:**
> ```
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
    Subsystem: CLEVO/KAPOK Computer Device 5140
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

``` I get this, I know it doesn't work properly because when I uninstall it and let the experimental driver be used some old games work, unfortunately it is not good enough for newer games with 3d support and higher effects. I also get downgraded to the really old version of ubuntu desktop and can't use the unity (not that I want to cause it sucks).
Well, as you can see from your lspci output the nvidia driver IS in use. Some old nvidia cards (in the GeForce 5xxx and 7xxx series) just don't work properly with the nvidia driver.

---

### Post by freeallforever on 2011-07-20
> **jocko said:**
> Well, as you can see from your lspci output the nvidia driver IS in use. Some old nvidia cards (in the GeForce 5xxx and 7xxx series) just don't work properly with the nvidia driver.
Then I don't understand why some of my games won't even turn on and some old games won't recognize any video mode with the nvidia driver. I bought all new parts this year.

---

### Post by jocko on 2011-07-20
> **freeallforever said:**
> Then I don't understand why some of my games won't even turn on and some old games won't recognize any video mode with the nvidia driver. I bought all new parts this year.
What graphics card do you have? Your lspci output wasn't very helpful...

---

### Post by freeallforever on 2011-07-20
> **jocko said:**
> What graphics card do you have? Your lspci output wasn't very helpful...
*nVidia GT 540M 1024MB PCI-Express GDDR3 DX11 *

---

### Post by jocko on 2011-07-21
Hmmm... I see it's a laptop. It doesn't happen to be one with a hybrid graphics solution (nvidia optimus)?
In that case, I think you are pretty screwed. I don't think nvidia will ever try to make optimus work with linux, so the open source drivers are probably the only usable drivers for you... Unless your bios allows you to inactivate the integrated gpu.

---

### Post by freeallforever on 2011-07-22
> **jocko said:**
> Hmmm... I see it's a laptop. It doesn't happen to be one with a hybrid graphics solution (nvidia optimus)?
In that case, I think you are pretty screwed. I don't think nvidia will ever try to make optimus work with linux, so the open source drivers are probably the only usable drivers for you... Unless your bios allows you to inactivate the integrated gpu.
Yes I have that, I will have to look at the bios then once I figure out how not to break something. :P

---

