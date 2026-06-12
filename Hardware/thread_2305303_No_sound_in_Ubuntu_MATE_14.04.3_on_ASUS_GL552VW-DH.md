---
title: "No sound in Ubuntu MATE 14.04.3 on ASUS GL552VW-DH71"
date: 2015-12-04
forum: Hardware
---

### Post by ncanna1 on 2015-12-04
Hi all,

I just purchased a new laptop for work, popped my old SSD into it, and installed Ubuntu MATE.  The system is putting out no sound whatsoever, and I've been through the common troubleshooting steps of force reloading alsa, reinstalling pa and alsa, editing /etc/modprobe.d/alsa-base.conf, etc.  Nothing is muted in alsamixer, and the input and output channels don't appear as muted in pavucontrol either.  

If I start a program playing sound, the application shows up in the sound settings tab.  The levels in pavucontrol show that there should be audio coming out, but there's just nothing.  Also worth noting that the sound works fine in Windows 10.

Here's some diagnostics (with some overlap):

**inxi -Fxz**:
```
System:    Host: nick-worktop Kernel: 3.16.0-55-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: MATE 1.8.2  Distro: Ubuntu 14.04 trusty
Machine:   Mobo: ASUSTeK model: GL552VW version: 1.0 Bios: American Megatrends version: GL552VW.210 date: 09/01/2015
CPU:       Quad core Intel Core i7-6700HQ CPU (-HT-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 20736.2 
           Clock Speeds: 1: 2600.00 MHz 2: 2600.00 MHz 3: 800.00 MHz 4: 800.00 MHz 5: 1600.00 MHz 6: 800.00 MHz 7: 800.00 MHz 8: 2600.00 MHz
Graphics:  Card: Intel Device 191b bus-ID: 00:02.0 
           X.Org: 1.15.1 drivers: fbdev,intel (unloaded: vesa) Resolution: 1920x1080@77.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits) GLX Version: 2.1 Mesa 10.1.3 Direct Rendering: Yes
Audio:     Card: Intel Device a170 driver: snd_hda_intel bus-ID: 00:1f.3 Sound: ALSA ver: k3.16.0-55-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: d000 bus-ID: 03:00.1
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Intel Wireless 7265 driver: iwlwifi ver: in-tree: bus-ID: 02:00.0
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 1120.2GB (11.4% used) 1: id: /dev/sdb model: HGST_HTS721010A9 size: 1000.2GB temp: 29C 
           2: id: /dev/sda model: Samsung_SSD_840 size: 120.0GB temp: 0C 
Partition: ID: / size: 94G used: 6.7G (8%) fs: ext4 ID: /boot size: 504M used: 79M (17%) fs: ext2 
           ID: swap-1 size: 17.18GB used: 0.67GB (4%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 66.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 218 Uptime: 1:20 Memory: 3723.0/15944.4MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 
```

**lspci -knn | grep -iA2 Audio **:
```
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:a170] (rev 31)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1c5d]
	Kernel driver in use: snd_hda_intel
```

**aplay -l**:
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20751/2 Analog [CX20751/2 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

**cat /proc/asound/cards**:
```
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xdf328000 irq 144
```

**amixer**:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 74
  Mono: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 7
  Mono: Playback 3 [43%] [-16.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 74 [92%] [0.00dB] [on]
  Front Right: Capture 74 [92%] [0.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [36.00dB]
  Front Right: 3 [100%] [36.00dB]
```

I struggled with this for about 5 hours scouring the net last night and am out of ideas.  Please help!

---

### Post by ncanna1 on 2015-12-06
Also, just to clarify, I'm not getting sound out of the built-in speakers, headphones plugged into either the out or in jack, or a wireless bluetooth speaker.

---

