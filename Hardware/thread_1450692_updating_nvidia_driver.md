---
title: "updating nvidia driver"
date: 2010-04-09
forum: Hardware
---

### Post by ankit singh on 2010-04-09
i have ubuntu 9.10 and have nvidia 185.x.x driver and i want upgrade it to 195.x.x.
earlier experiments with this lead me to a crash system. i have a bad experience of watching video in karmic. Video gets torn in middle (like a photograph torn in middle and than joined using tapes. Here instead of tapes a thin black line appears). I am not sure know whether this problem is driver based or because of something else but i want to see if upgrading driver helps.

---

### Post by diesch on 2010-04-09
On [https://launchpad.net/~nvidia-vdpau](https://launchpad.net/~nvidia-vdpau) there's a PPA containing up to date packages for nVidia graphic drivers. 

Note that this packages are not supported by the Ubuntu team may cause problems, especially when updating to a new release.

For me they are working fine so far.

---

### Post by lidex on 2010-04-09
> **ankit singh said:**
> i have ubuntu 9.10 and have nvidia 185.x.x driver and i want upgrade it to 195.x.x.
earlier experiments with this lead me to a crash system. i have a bad experience of watching video in karmic. Video gets torn in middle (like a photograph torn in middle and than joined using tapes. Here instead of tapes a thin black line appears). I am not sure know whether this problem is driver based or because of something else but i want to see if upgrading driver helps.

If you're using compiz, disable visual effects during video playback.
What is the output of this command:
```
lspci -nn | grep VGA
```

---

### Post by ankit singh on 2010-04-10
> **lidex said:**
> If you're using compiz, disable visual effects during video playback.
What is the output of this command:
```
lspci -nn | grep VGA
```


00:10.0 VGA compatible controller [0300]: nVidia Corporation C73 [GeForce 7050 / nForce 610i] [10de:07e3] (rev a2)

---

### Post by ankit singh on 2010-04-10
:(  updating driver has again not solved this problem neither disabling video effect in compiz  helps. anybody here knows why this happens  :confused:

---

### Post by diesch on 2010-04-10
What program do you use the play the video?

---

### Post by lidex on 2010-04-10
Is your driver showing as enabled in "hardware drivers"? Do you have "nvidia-settings" installed? Have you tried running:
```
sudo nvidia-xconfig
``` to generate xorg.conf?

---

### Post by ankit singh on 2010-04-11
i have generated new xorg.conf . I have used vlc,xbmc,totem all of them have same problem.

---

### Post by lidex on 2010-04-11
Did you reboot after xorg.conf reconfigure? Go to nvidia-settings="System>Administration>Nvidia XServer Settings" and navigate to "X Server XVideo Settings". Enable "Sync to VBlank"

---

### Post by ankit singh on 2010-04-11
yes i rebooted my pc. i am giving up. I am planning to move to 9.04 comming weekend

---

