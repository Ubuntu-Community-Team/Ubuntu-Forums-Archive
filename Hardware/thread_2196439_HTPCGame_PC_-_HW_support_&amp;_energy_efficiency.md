---
title: "HTPC/Game PC - HW support &amp; energy efficiency"
date: 2013-12-29
forum: Hardware
---

### Post by alex2399 on 2013-12-29
Somewhere next year I wish to build myself a new PC. Though I am not sure if there are hardware quirks that will seriously ruin the fun.

Currently I am using an older PC mainly used for gaming and typical desktop work. It consists of:

AMD Athlon X2 5600+ @2,8Ghz
Gigabyte MA790X-DS4 mainboard
2*2GB Ram
Asus ATI Radeon HD3870 512MB
1*1TB HD, 
1*500GB HD
An analogue TV card

This PC was intended as a gaming PC and performance wise it still fulfills my (gaming) needs. But it draws way too much power in idle, ~about 140W. While playing a video or just doing mundane tasks about 200W. When I am playing an intensive 3D game even more. Though I recently got idle power down to 90W by using kernel 3.12 and Radeon DPM.
Furthermore I am a very unhappy customer of the Radeon HD3870. AMD/ATI driver support in Linux systems was & is seriously lacking, it only worked as it should IIRC with Ubuntu 10.04 for me. I will spare you the frustrations of this card while being used in Linux. So for my next PC I am seriously leaning towards Nvidia.

Next PC will be placed in the living room and the majority of the day turned on. So power efficiency is important. It will be connected to a FullHD TV mainly to watch satellite television. Furthermore I wish to connect two monitors (Samsung 206BW, 1680*1050) for doing more serious desktop work. Software used will probably be Kubuntu and XBMC. For games Windows 7.

Currently I have this setup in mind
CPU: Pentium G3220
MB: MSI B85M-G43
Ram: probably 2*4GB
GPU: Integrated + Nvidia GTX650 Ti Boost 2GB (preference) or ATI Radeon HD7850 2GB
HD's from previous PC and a cheap SSD.
DVB-S2 Receiver: TBS6982 dual tuner

Regarding this setup, I have some questions concerning hardware support.

I wish to physically connect the IGP graphics to the TV, the discrete card to the monitors. When I am only using the TV to watch satellite programs, recorded movies, browsing, reading or writing etc... is it possible to completely power down the discrete graphics card? Without rebooting or some other flaky methods.  I read about some projects (VGA switcheroo, Bumblebee, Ironhide) but I am unsure of their current state and if it will even work since a lot of them seem to be aimed at laptop use.

Do the Intel Linux drivers for the IGP work correctly for decoding movie material?

Is it possible to use the discrete GPU for rendering on the TV via the IGP connector? Otherwise, do current GPU cards support triple monitors when they have the physical connections?

I hear great things about the Nvidia proprietary drivers, do they really work that well and do they still support older hardware? Since I do not wish to be left in the dark within the forseeable future. While I am at it, what is the current state of the open source Nouveau driver? Does it handle all mundane desktop work and manage power consumption?

Got some horror stories of Linux & Nvidia/Intel that I should know of?

In regards to the DVB-S2 tuner, got some other recommendations? I am looking for a card that has good support in Linux, is able to power down the LNB's when not using the tuner, is stable and has good picture quality. Preferably it's drivers are open-source. Currently I own an Technisat Technistar S2+ standalone receiver, I wish to have the same quality from a PC card.

If anybody has the TBS6982 or a similar single/dual tuner TBS model, how does it work? Zapping times, sensitive enough, power consumption etc...?

---

