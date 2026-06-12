---
title: "sound stops working after 2min - without error message"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by almoehi on 2007-02-09
Hi,
I have installed edgy recently and everything works well - except for the sound.
If I play some music (xmms, firefox, mplayer ...) it plays well for about 2min, then the sound stops working completely (my connected USB mouse also stops working).
The card did work on my previous gentoo system.

Sadly there isn't any message in the syslog / dmesg etc.

lspci:
```
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev f6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra 
nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address  
Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con 
troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella 
neous Control
01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5650]  
(rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ether 
net Controller (rev 13)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ab)
02:01.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ab)
02:01.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 03)
02:01.3 System peripheral: Ricoh Co Ltd R5C576 SD Bus Host Adapter (rev 01)
02:01.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN  
Controller (rev 03)

```

lsmod | grep snd:

```
snd_intel8x0           33436  0 
snd_ac97_codec         96672  1 snd_intel8x0
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0 
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe 
r_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
```


I searched the net but by now did not find any solution(s) so hopefully someone can help?

---

