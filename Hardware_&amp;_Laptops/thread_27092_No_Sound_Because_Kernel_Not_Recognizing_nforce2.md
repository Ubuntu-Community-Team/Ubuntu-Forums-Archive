---
title: "No Sound Because Kernel Not Recognizing nforce2?"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by blahblahblah on 2005-04-14
I have just installed Hoary on a new PC I built. The box has a Chaintech 7NJL6 mobo which is nforce2 based. The installed proceeded without error, but there is no sound. I've played with the various mixers and sound is not muted and the volume is up. 

Everything else on the box is working fine. I don't know if the problem is Linux, Ubuntu, or the hardware. Does anyone have any ideas? Help!

lspci returns the following, which makes me wonder if the hardware is being recognized properly:

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0080 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0084 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 0087 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 0087 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 0088 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 008a (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation: Unknown device 008b (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation: Unknown device 0085 (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
0000:01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 300/305 PCI/AGP VGA Display Adapter (rev 90)

dmesg had the following lines related to sound:
intel8x0_measure_ac97_clock: measured 49902 usecs
intel8x0: clocking to 47431

lsmod returned the following lines related to sound:
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

---

### Post by Dracontopes on 2005-04-15
I have the same sound chipset you are using. The snd-intel8x0 driver uses ALSA (I think) so you might want to set everything to ALSA in gstreamer-properties.

However, this is what lspci says here:

```

chris@chris:~ $ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:01:0b.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
0000:02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
0000:03:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]
0000:03:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9700 Pro] (Secondary)

```

Kernel version: 2.6.11-1-k7

---

### Post by blahblahblah on 2005-04-17
Okay. I got it. I needed to run alsamixer and mute the IEC958 Capture Monitor.

---

### Post by gizmospc on 2005-04-29
[QUOTE=blahblahblah]Okay. I got it. I needed to run alsamixer and mute the IEC958 Capture Monitor.[/QUOTE]

Thanks - I also needed to do the same thing.  You saved me from pulling my hair out!   =D>

---

