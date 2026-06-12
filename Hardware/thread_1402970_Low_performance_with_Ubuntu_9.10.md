---
title: "Low performance with Ubuntu 9.10"
date: 2010-02-09
forum: Hardware
---

### Post by nomadewolf on 2010-02-09
Hi!
I have the latest Ubuntu installed on my system, but i seem to experience some kind of performance lag... This is most noticeable when i watch videos (avi, mkv, etc) and when i switch from window mode to fullscreen mode the sound keeps going while the image satys still for a few seconds (4, exactly until it gets to fullscreen and another 4 to the image starts playing again)... This is most anoying and i would like to know if there's a way to solve this...
My laptop is an Asus X50SL with ATI 3470 graphics card. I have the ATI proprietary drivers installed and the system up to date, so i don't know what else to do... Someone help, please...
I've also tried different players and messing with the graphics card definitions. In windows the performance is normal, only in Ubuntu i get this kind of lag... I know it&#347; not a powerfull machince, but it should be enough...

---

### Post by sanderj on 2010-02-09
If your laptop has the specs below, it *is* a powerful machine, and you should have good performance. However, I don't know what's causing your problems. Start by running System -> Administration -> System Monitor, and look at:
Processes: which process is the highest CPU usage
Resources: CPU and memory usage




Intel Core 2 Duo T5550
ATI Mobility Radeon HD 3470
2 GB Memory
250 GB HDD

---

### Post by ivanvajar on 2010-02-09
1. System/Preferences/Multimedia Systems Selector
2. In 'Video' tab choose 'X Window Sustem (no Xv)' for default output plugin

If that doesn't work, try the other plugins.

---

### Post by nomadewolf on 2010-02-10
> **sanderj said:**
> If your laptop has the specs below, it *is* a powerful machine, and you should have good performance. However, I don't know what's causing your problems. Start by running System -> Administration -> System Monitor, and look at:
Processes: which process is the highest CPU usage
Resources: CPU and memory usage




Intel Core 2 Duo T5550
ATI Mobility Radeon HD 3470
2 GB Memory
250 GB HDD

The process with the highest CPU usage is Firefox
CPU usage tops at about 35%
And memory at about 1GB out of 3GB

Everything seems pretty normal to me...

---

### Post by nomadewolf on 2010-02-10
> **ivanvajar said:**
> 1. System/Preferences/Multimedia Systems Selector
2. In 'Video' tab choose 'X Window Sustem (no Xv)' for default output plugin

If that doesn't work, try the other plugins.

Can't find: System/Preferences/Multimedia
But changing the plugins in VLC didn't seem to have any effect.
I experience a lag when i have Firefox minimized on the task bar and try to open the window again... So i don't think is multimedia related. The 'slowness' is general...

---

