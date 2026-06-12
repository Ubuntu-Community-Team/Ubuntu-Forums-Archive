---
title: "sound very low with intel8x0"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by jamdess on 2007-10-21
Hi,

The sound is very low on my laptop Medion MD6015. 
I've compile and install the new alsa-driver (1.0.15) libs, oss and utils, but i still have a very very very low sound.

here is my lspci :
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:06.0 Communication controller: Intel Corporation 536EP Data Fa
x Modem
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
00:0d.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
```

My asoundconf list
```
Names of available sound cards:
SI7012
```

aplay -l
```
**** Liste des PLAYBACK périphériques ****
carte  0: SI7012 [SiS SI7012], périphérique 0 : Intel ICH [SiS SI7012]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
```

I've compile the alsa-drivers with this option
./configure --with-cards=intel8x0 --with-sequencer=yes

And modify the alsa-base file like this
```
# ALSA portion
alias char-major-116 snd
options snd cards-limit=1
alias snd-card-0 snd-card-intel8x0

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss 
```

Could you help me ?


ps: i'm really sorry for my 'bad english"

---

