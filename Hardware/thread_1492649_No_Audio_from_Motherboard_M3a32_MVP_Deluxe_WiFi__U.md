---
title: "No Audio from Motherboard M3a32 MVP Deluxe Wi/Fi / Ubuntu Lucid 10.4"
date: 2010-05-25
forum: Hardware
---

### Post by Austiclees on 2010-05-25
**Intro:** Let me start by saying I've spent two days researching this issue and resolution. I am a noob to Linux, but I've done tons of research as I like to resolve my issues on my own. From the time I've spent with Ubuntu 10.4 Lucid over the past couple of weeks, I'm loving it and want to stick with it. I have it dual booting on my Laptop with no issues.

**System:** 
Motherboard: M3a32-MVP Deluxe Wi/Fi
Video Card: ATI Radeon 3870 512 GB
Ram: 8GB corsair (4x2GB)
HDD: Uh, several, there are 5 HDD's installed on my system with several OS's.

**Problems:** No Audio from MB, Raid controller not working.
My main concern right now is my audio. I have 2 512 GB Maxtor drives in Raid0 running Win7 Ultimate that I can't access, but like I said, the audio is more important.

I have audio coming from the HDMI port in the video card, but it's choppy. I'd rather use my MB's audio device anyway so I can utilize my surround sound system. I've obtained the Linux drivers from ASUS but don't know how to install them. Besides that, in sound preferences, it appears to be loaded and I've tried every combination of settings possible. And before you ask.. It's not muted, (this seems to be the typical first smart a$$ response to noobs regarding sound).

**aplay -l**
```
austiclees@Austiclees-Linux-Desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

**LSPCI**
```
austiclees@Austiclees-Linux-Desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:0b.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx1 port A)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 RAID bus controller: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 RAID bus controller: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
04:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
04:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
05:06.0 Multimedia controller: ATI Technologies Inc Device 4d50
05:08.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
```

**Conclusion:**
I'd appreciate any help the community could provide. If I've left anything out please let me know. My goal was to provide as many details as I could. Thanks again.

---

