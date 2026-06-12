---
title: "MSI WIND u135 wifi problems"
date: 2010-09-11
forum: Hardware
---

### Post by vy13 on 2010-09-11
Hi,
A few days ago i bought MSI WIND U135. It is with Win7 but i want to put Linux on it. I tried Ubuntu Netbook and the wifi & webcam didnt work. EasyPeasy - wifi didnt work.
Mandriva freezes at boot, Fedora Mobilin - no wifi, Mint 9 KDE - no wifi. The only distro that worked was Jolicloud! Oh, and MeeGo. But I want full desktop so (with working wifi!) Can somebody please help me about choosing a distro with working wifi, webcam etc... ? Thanks in advance!):P:p

---

### Post by clipt on 2010-09-18
i hit Fn F11 when mine booted up and it worked.

---

### Post by taffy-nay on 2010-10-04
The wireless chipset used by the onboard WiFi in the u135 is rt3090.

do the following

open a terminal

```
sudo add-apt-repository ppa:markus-tisoft/rt3090
```

then

```
sudo apt-get update
```

then open update manager 

*System > Administration > Update Manager*

Run the update and this will install rt3090-dkms.

In the terminal, type

```
sudo modprobe rt3090sta
```

This should sort out your wireless issues (until you do a kernel update and then have to go through this all over again).

I have made absolutely **zero** headroom on getting the webcam to work though

---

### Post by gds on 2010-10-05
Excellent! Thanks taffy-nay. I was manually installing a rt3800 module I found, this is much better.

The webcam works me. I activate it with Fn-F6 and it is detected as a "BisonCam, NB Pro (5986:0141)". Capturing stills seems OK, but video has a ridiculously low frame rate and saturates the CPU using Cheese. Using mencoder gave me good results, though (both audio & video).

---

