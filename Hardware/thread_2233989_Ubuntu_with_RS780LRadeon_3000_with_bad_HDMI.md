---
title: "Ubuntu with RS780L/Radeon 3000 with bad HDMI?"
date: 2014-07-11
forum: Hardware
---

### Post by redpenguinmail on 2014-07-11
My buddy and I are working on a brand new built Quad-Core AMD with the following Graphics Adapter:


01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]

Out of the box, Ubuntu seems to work with the HDMI with mirroring just fine with 14.04.

Yet if you change the channel or turn off the TV, then sudden it never gets the resolution correct or no signal.

I have Googled this card and for some reason it's considered "legacy" yet this is a brand new bought motherboard from NewEgg this week, go figure....

I have tried using the legacy drivers which fail to install because I think I am using them on too new of Ubuntu then it was designed for.

Anyway to use this graphics card without having to go to an older version of Ubuntu or something?

---

### Post by patsev-anton on 2014-07-12
lspci -knn | grep VGA -A2

---

### Post by Mark Phelps on 2014-07-12
> it's considered "legacy" AMD dropped support for this card, and all the other 2x/3x/4x-series cards, last summer; that's why it's considered "legacy".

The fglrx drivers that work with this card won't work with any Ubuntu version newer than 12.04.1.  Newer versions of ubuntu have an upgraded X-server version that is incompatible with the fglrx drivers used by these cards.

---

### Post by redpenguinmail on 2014-07-12
> **patsev-anton said:**
> lspci -knn | grep VGA -A2

01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000] [1002:9616]
        Subsystem: ASUSTeK Computer Inc. Device [1043:8388]
01:05.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RS780 HDMI Audio [Radeon (HD) 3000 Series] [1002:960f]

---

### Post by redpenguinmail on 2014-07-12
My buddy and I installed 12.04.1 and with a PPA for fglrx-legacy and installing PulseAudio we are up and running perfectly.

Would be nice to be able to upgrade the Ubuntu version but MythTV seems to hint we can upgrade it without upgrading the underlying distro all the time. So we should be good for a while anyway.

---

### Post by redpenguinmail on 2014-07-13
We now have another problem.

When you play TV recordings from MythTV in MythTV and VLC, you get like a "jittering" during fast motion, yet sound keeps up.

---

