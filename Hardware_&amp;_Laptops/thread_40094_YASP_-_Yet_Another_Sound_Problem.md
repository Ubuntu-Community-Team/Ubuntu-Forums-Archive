---
title: "YASP - Yet Another Sound Problem"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by navajo on 2005-06-07
I know that the Internet and the Ubuntu Forums are full of How-To's and Tips&Tricks, but for me, no guide worked.  :-# 
After KDM starts, I get this message: 
> device: default can't be opened for playback (Device or resource busy)
Still, the device is not in use by anyone:> iulian@navajo:~$ lsof /dev/dsp
iulian@navajo:~$ lsof /dev/snd/*
iulian@navajo:~$     
I've installed the NFORCE sound drivers from [http://nvidia.com](http://nvidia.com), modprobed nvsound, restarted /etc/init.d/alsa... followed their every step in the instructions README... nothing... I don't know what to do next...

Here's my system:> iulian@navajo:~$ [b]uname -r
2.6.10-5-k7[/b]
iulian@navajo:~$> iulian@navajo:~$ **lspci**
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
**0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)**
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:0d.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 61)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
Please help me, as I'm getting nuts.  ](*,)

---

### Post by gcranston on 2005-06-08
[QUOTE=navajo]I know that the Internet and the Ubuntu Forums are full of How-To's and Tips&Tricks, but for me, no guide worked.  :-# 
After KDM starts, I get this message: 

Still, the device is not in use by anyone:
I've installed the NFORCE sound drivers from [http://nvidia.com](http://nvidia.com), modprobed nvsound, restarted /etc/init.d/alsa... followed their every step in the instructions README... nothing... I don't know what to do next...

Here's my system:
Please help me, as I'm getting nuts.  ](*,)[/QUOTE]
 try turning off the boot up sounds.  This locked up my sound card for the entire session.  

I am still stuck with the problem that only application can run sound at a time.  ie.  No ingame sound with a music player going at the same time.  Also can't play a movie file with a music player going (mplayer hangs till I stop playback in xmms).
using a -->Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)


All situations give /dev/dsp Device or Resource busy.

Any help?

---

### Post by navajo on 2005-06-09
10x for your reply, but my sound still doesn't work...

---

### Post by solkar_saruman on 2005-06-11
Same problem here.

I tried this...
> root@SpongeBob:/home/solkar # cat /proc/asound/cards
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with unknown codec at 0xd0000c00, irq 10 
That unknown codec line. Could be the problem?

My System:

> root@SpongeBob:/home/solkar # lsmod|grep snd
snd_intel8x0m          18372  0
snd_intel8x0           32352  0
snd_atiixp             19972  0
snd_ac97_codec         74144  3 snd_intel8x0m,snd_intel8x0,snd_atiixp
snd_pcm_oss            52132  0
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  5 snd_intel8x0m,snd_intel8x0,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  8 snd_intel8x0m,snd_intel8x0,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  1 snd
snd_page_alloc          9732  4 snd_intel8x0m,snd_intel8x0,snd_atiixp,snd_pcm 

> root@SpongeBob:/home/solkar # lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers(rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 855GME GMCH Host-to-AGP Bridge (Virtual PCI-to-PCI) (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller(rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev03)
**0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)AC'97 Audio Controller (rev 03)**
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0000:02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)0000:02:04.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:02:06.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:02:06.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:02:06.3 Unknown mass storage controller: Texas Instruments: Unknown devi

---

### Post by navajo on 2005-06-16
I solved my problem. I bought a 9 EUR PCI sound card and it works like a charm...
But another thing bothers me now... no software seems to knowhow to put the sount in my 6 speakers. What gives?

---

