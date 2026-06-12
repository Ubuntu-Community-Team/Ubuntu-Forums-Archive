---
title: "Xine &amp; Beep-Media-Player sound conflict"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by SadaraX on 2005-10-11
Hello. I am trying to configure xine and beep-media-player to work at the same time properly without crashing. I have them both set to use ALSA drivers (alsa-base version 1.0.8). I am not stuck on using ALSA, it just seemed to work better than OSS, but if I can get that to work, I will use it. 

I cannot remember having this problem in other distros of linux I tried, but there's always a first time. Basically, I play any audio in beep-media-player, then start xine up with a video file. The video file plays with no sound and hangs up after about 5 seconds, thought bmp continues to play the audio just fine. 

When playing a xine video, and then trying to play a file in bmp, beep-media-player refuses to play saying:
"Please check that:
1. You have the correct output plugin selected 
2. No other program is blocking the soundcard
3. Your soundcard is configurd properly"

In this case, bmp is using ALSA plugin 0.9.7 for output, and the configuration on the plugin is:

Audio device: default
Mixer card: NVidia CK804
Mixer Device: PCM
Buffer time(ms): 500
Period time(ms): 50
Mmap Mode: Check

Xine audio settings are: 
alsa_hw_mixer(*): check
audio driver to use: alsa
alsa mixer device: pcm
sound card can do mmap -- device.alsa_mmap_enable(*): check

I am using xine 0.99.3 and bmp 0.9.7 ubuntu packages. I am running Kubuntu 5.04. My system specs:

> Motherboard: EPOX EP-9NPA+Ultra NF4 ULTRA RT

Video Card: Geforce 6800GT 256MB DDR PCI Express x16 Video Card - ASUS EN6800/TD/256
	Type VGA XFX|
	Model PVT45GUDF3

CPU: AMD Athlon 64 X2 4200+ Manchester 2000MHz FSB Socket 939 Dual Core
	Processor Model ADA4200BVBOX

RAM: CORSAIR XMS 1GB 184-Pin DDR SDRAM DDR 400 (PC 3200) Unbuffered System
	Memory Model CMX1024-3200C2PT
	Model #:CMX1024-3200C2PT

UPDATE: This problem as been solved. By setting alsa-utils to startup as a sound daemon when my system boots, and setting all my applications to use ALSA as their sound driver, it fixed the conflict.

---

