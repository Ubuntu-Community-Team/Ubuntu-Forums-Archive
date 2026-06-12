---
title: "Problem with sound"
date: 2014-11-23
forum: Hardware
---

### Post by milda81 on 2014-11-23
Hi, i have notebook Haier L51AI1. I've installed Ubuntu Mate 14.04.1 LTS. If I play any music/video, i hear sound from headphones, but from speakers no. Can anybody help me? (sorry from my bad English).

```
milda81@milda81:~$ sudo aplay -l
[sudo] password for milda81: 
**** Seznam PLAYBACK Hardwarových za&#345;ízení ****
karta 0: SB [HDA ATI SB], za&#345;ízení 0: ALC883 Analog [ALC883 Analog]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 0: SB [HDA ATI SB], za&#345;ízení 1: ALC883 Digital [ALC883 Digital]
  Podza&#345;ízení: 1/1
  Podza&#345;ízení #0: subdevice #0
karta 0: SB [HDA ATI SB], za&#345;ízení 6: Si3054 Modem [Si3054 Modem]
  Podza&#345;ízení: 0/1
  Podza&#345;ízení #0: subdevice #0
```


```
milda81@milda81:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC410 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 1
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 3
00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 83)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RC410M [Mobility Radeon Xpress 200M]
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
08:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
```

Thanks for every help.

---

### Post by ajgreeny on 2014-11-23
If mate uses pulseaudio open the **pulseaudio-volume-control**, probably from the volume panel icon- Sound Settings and there you may find that speakers are listed separately from headphones in the **Output devices** tab, and may be able to raise the volume or unmount the speakers.

---

### Post by milda81 on 2014-11-24
Thank you, but I'm use ALSA. On alsamixer - every volume is up. On WinXP - speaker works perfect.

---

### Post by milda81 on 2014-11-24
Here is my ALSA script:
[http://www.alsa-project.org/db/?f=b324da3c1ffc0e78a0223332e62cf5a1ccdd7575](http://www.alsa-project.org/db/?f=b324da3c1ffc0e78a0223332e62cf5a1ccdd7575)

---

