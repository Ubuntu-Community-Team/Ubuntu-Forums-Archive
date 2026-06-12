---
title: "Intermittent HDMI Audio using AMD HD 7950 and Ubuntu 13.04"
date: 2013-04-30
forum: Hardware
---

### Post by maissiou23 on 2013-04-30
Do anyone know how to resolve intermittent HDMI audio problem with AMD Radeon HD 7950?
I installed the latest Catalyst drivers (13.4) and the problem still persists. Audio is intermittent. Every 1-2 seconds, I have a drop/audio freeze.

I made sure that the problem is with the HDMI drivers, since when I put the headphones Jack at the rear (motherboard) audio play just fine. Same from front panel (case) audio connectors. I can also tell that the application (VLC), Pulse, ALSA works just fine. So the problem is really with AMD HDMI audio drivers.

I tried to allso to 
      - add "radeon.audio=1" to /etc/default/grub 
     - updating ALSA drivers
     - Change video drivers (xorg-edgers, ppa and the .run for Catalyst 13.4)

..... Still nothing. 

Could someone point my out to how I can solve this problem? ...may be the sampling rate of AMD HDMI Audio drivers?

---

### Post by ppjdee on 2013-05-01
I had the same issue, drivers made no difference. But I found a thread about updating to the 3.9 kernel, it fixed my audio problems.
[http://ubuntuforums.org/showthread.php?t=2140898](http://ubuntuforums.org/showthread.php?t=2140898)

---

### Post by mazipha on 2013-06-15
Hello,

I have the exact same problems with my AMD 7950 card. I've installed the latest catalyst driver and I have an audio freeze every 2 seconds with HDMI sound.
Sound from the motherboard is fine.

Did anyone succeed solving this problem ?

---

### Post by Yellow Pasque on 2013-06-15
If you want to try latest kernel module/driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by mazipha on 2013-06-16
> **Temüjin said:**
> If you want to try latest kernel module/driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
Already tried that and I still have the problem. I've the last catalyst driver also.
The strange thing is that the sound drop is very regular. It actually goes with a pattern like that:
sound during 5 secondes then sound stop for half a second then sound for 5 seconds, and goes always with this pattern.
 
Is there no work around to have soun over HDMI ?

---

### Post by Yellow Pasque on 2013-06-16
The only other workaround I can think of in this case is: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

