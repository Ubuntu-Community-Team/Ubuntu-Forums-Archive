---
title: "Ubuntu 9.10 audio problem"
date: 2010-01-01
forum: Hardware
---

### Post by epz on 2010-01-01
Hello everyone,

i recently bought a compaq presario cq60 415sl but i noticed that there are some little (BIG) problems with hardware.

I used this pc all the time mostly for work but in the last days I wanted to have some fun with games (wormux, hedgewars, and some on wine, just saying) but, after about 2 minutes of playing audio goes, initially it works great but then goes, without any reason, started to be bad and then disappears. At game restart or relog of user it comes back again.

I'm not hiding you that I searched for an exorcist in my area but didn't find any, then when brain restarted to work I got that the problem might be hardware, either chipset or audio card.

Here some details. (im afraid my language isn't that easy to understand but I suppose you can recognize models anyways, don't make me change language be nice ^^)

```
 APLAY -L

scheda 0: NVidia [HDA NVidia], dispositivo 0: CONEXANT Analog [CONEXANT Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: NVidia [HDA NVidia], dispositivo 1: Conexant Digital [Conexant Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: NVidia [HDA NVidia], dispositivo 3: NVIDIA HDMI [NVIDIA HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
```


```
LSPCI

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```


```
CODECS

Codec: Conexant CX20561 (Hermosa)
Codec: Nvidia MCP78 HDMI
```

Could anyone give me some hints on how to solve this please? (except throw your pc from the window, I thought that but my money tree is not working:lolflag:)

ps: hope you will excuse me for any mistake in my post, I'm a bit still on 1st january, and if I can "happy 2010 to you all"

---

### Post by epz on 2010-01-01
I have to assume that there isn't a solution?

---

### Post by epz on 2010-01-02
up

---

### Post by epz on 2010-01-03
up  I'd really like an answer, I got 94 views but no answer, is my case so desperate??

---

### Post by SecretCode on 2010-01-03
One day isn't enough to conclude that there's no answer. 

You do need to bump threads because there are so many new ones here that yours will get lost ... but it doesn't do much good bumping within the same day, just looks impatient.

Anyway ... I have the same problem. Sound is fine normally, but sound from some games gets choppy and stops, sometimes within a few seconds.

---

### Post by epz on 2010-01-03
eer yes sorry you are right, I tried to follow the 24 hours delay but.  1 the first post was in the night and i prefered to avoid respect all 24 hours (can image why)  2 I gone down so i upped  anyways I'd have to say sorry to the ubuntuforums staff for that (don't hate me pleeease :D)

---

### Post by epz on 2010-01-04
up

---

### Post by Bowen_linux on 2010-01-04
If I am not wrong the sound card you're currently using is HDMI. Go to sound preferences, output, and select the one without HDMI. I had a problem similar to yours and that fixed my problem...good luck :popcorn:

---

### Post by SecretCode on 2010-01-05
I hope that sorts it out for **epz** - but I don't have HDMI. Only one card appears in prefs > sound > output ("Internal Audio Analog Stereo").

My sound details are:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
```

```
$ lspci
...
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
...
```

```
$ sudo lshw -C sound
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f0a00000-f0a03fff
```

```
$ sudo cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC268
Codec: Motorola Si3054
```

So ... any advice for my situation (same problem)?

---

### Post by epz on 2010-01-08
> **Bowen_linux said:**
> If I am not wrong the sound card you're currently using is HDMI. Go to sound preferences, output, and select the one without HDMI. I had a problem similar to yours and that fixed my problem...good luck :popcorn:

 hdmi wouldn't play any sound if i choose that, i choose either duplex or output (Internal Audio Analog Stereo)

@secret code

do you have a laptop too?? this is the classical examples of laptops windows vista/7 ONLY....

Am I blind or they write windows vista/7 ready??? should work with linux, and worst of all, devices producers won't release official drivers for linux (not so bad, nvidia proprietary drivers times ago caused a privilege escalation in a 1 2 3 :D)

---

### Post by SecretCode on 2010-01-09
Yes, I have a laptop - but Ubuntu and XP only, no Vista/7.

---

