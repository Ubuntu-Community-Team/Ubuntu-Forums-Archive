---
title: "Sound Blaster Recon 3D don't work on Ubuntu 12.04"
date: 2012-08-06
forum: Hardware
---

### Post by ps3love on 2012-08-06
```
ps3@ps3-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1c.6 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 7 (rev c4)
00:1c.7 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Audio device: Creative Labs Device 0012 (rev 01)
02:00.0 USB controller: VIA Technologies, Inc. Device 3432 (rev 03)
03:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 30)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
06:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11)
07:00.0 VGA compatible controller: NVIDIA Corporation Device 1189 (rev a1)
07:00.1 Audio device: NVIDIA Corporation Device 0e0a (rev a1)
ps3@ps3-desktop:~$ 

```

```
ps3@ps3-desktop:~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: PCH [HDA Intel PCH], dispositivo 0: VT2020 Analog [VT2020 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 1: VT2020 Digital [VT2020 Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 2: VT2020 HP [VT2020 HP]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 7: HDMI 1 [HDMI 1]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 8: HDMI 2 [HDMI 2]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 9: HDMI 3 [HDMI 3]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0 

```

```
ps3@ps3-desktop:~$ cat /proc/asound/card*/codec* | grep -i codec
Codec: VIA VT2020
Codec: Nvidia GPU 40 HDMI/DP
```

```
ps3@ps3-desktop:~$ dmesg | grep -i hda
[    5.110257] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.110301] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[    5.110323] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    5.161310] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[    5.161374] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    5.161426] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    5.161473] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    5.161521] input: HDA Intel PCH Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    5.161568] input: HDA Intel PCH Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    5.161616] input: HDA Intel PCH Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    5.161796] snd_hda_intel 0000:07:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.161799] hda_intel: Disabling MSI
[    5.161834] snd_hda_intel 0000:07:00.1: setting latency timer to 64
[    5.767526] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:07:00.1/sound/card2/input12
[    5.767578] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:07:00.1/sound/card2/input13
[    5.767618] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:07:00.1/sound/card2/input14
[    5.767656] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:07:00.1/sound/card2/input15
```

```
ps3@ps3-desktop:~$ ps aux | grep pulse
ps3       2315  1.1  0.0 118560  6084 ?        S<l  14:56   0:20 /usr/bin/pulseaudio --start --log-target=syslog
ps3       2455  0.0  0.0  14084  2488 ?        S    14:56   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
ps3       4168  0.0  0.0   4392   828 pts/0    S+   15:25   0:00 grep --color=auto pulse

```

```
ps3@ps3-desktop:~$ lspci -v | grep Creative
01:00.0 Audio device: Creative Labs Device 0012 (rev 01)
	Subsystem: Creative Labs Device 0013
```

---

### Post by ps3love on 2012-08-07
up

---

### Post by Toz on 2012-08-07
This might be of interest: [http://www.phoronix.com/scan.php?page=news_item&px=MTEwNTg]("http://www.phoronix.com/scan.php?page=news_item&px=MTEwNTg").

---

