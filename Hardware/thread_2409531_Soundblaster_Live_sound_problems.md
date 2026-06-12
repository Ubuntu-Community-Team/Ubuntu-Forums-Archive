---
title: "Soundblaster Live sound problems"
date: 2019-01-03
forum: Hardware
---

### Post by Timothy Taylor on 2019-01-03
I have rebuilt my PC and reinstalled 18.04.1.

I can't get my sound working properly.  My early attempts using the "Sound" utility had system sounds, clicks, etc working fine, but no or v v poor audio from browser & media.

I recall issues with sound drivers (?) for this card in my previous PC, but it was working OK in this PC before the rebuild.
The previous issue was solved by changing audio software or driver (from Pulse Audio to Alsa?)  I have tried adding & removing these and now seem to have completely messed up my sound settings.

**aplay -l** gives the following output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SB Live! Value [CT4670]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SB Live! Value [CT4670]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SB Live! Value [CT4670]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I see from Sound Preferences that the "HDA NVidia" is selected by default which is confusing - I thought the NVidia card was graphics only ???

I no longer have the option to set up surround-sound with the SB card.

System Information:```

System:    Host: U-2 Kernel: 4.15.0-43-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: MATE 1.20.1 (Gtk 3.22.30-1ubuntu1) info: mate-panel dm: lightdm
           Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x serial: N/A BIOS: Award v: FA date: 04/23/2013
CPU:       6 core AMD FX-6300 Six-Core (-MCP-) arch: Bulldozer rev.0 cache: 12288 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 42186
           clock speeds: min/max: 1400/3500 MHz 1: 2515 MHz 2: 2244 MHz 3: 2077 MHz 4: 2339 MHz
           5: 2165 MHz 6: 2493 MHz
Memory:    Using dmidecode: root required for dmidecode
Graphics:  Card: NVIDIA GT218 [GeForce 210] bus-ID: 01:00.0 chip-ID: 10de:0a65
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1280x1024@75.02hz
           OpenGL: renderer: GeForce 210/PCIe/SSE2 version: 3.3.0 NVIDIA 340.107 Direct Render: Yes
Audio:     Card-1 NVIDIA High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1 chip-ID: 10de:0be3
           Card-2 Creative Labs EMU10k1 [Sound Blaster Live! Series]
           driver: snd_emu10k1 port: bf00 bus-ID: 04:06.0 chip-ID: 1102:0002
           Sound: Advanced Linux Sound Architecture v: k4.15.0-43-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: ce00 bus-ID: 03:00.0 chip-ID: 10ec:8168
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 3000.6GB (0.8% used)
           ID-1: /dev/sda model: ST3000DM007 size: 3000.6GB serial: <filter>
           Optical-1: /dev/sr0 model: HL-DT-ST DVDRAM_GSA-H10L rev: LX06 dev-links: cdrom,cdrw,dvd,dvdrw
           Features: speed: 40x multisession: yes
           audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r,dvd-ram state: running
Partition: ID-1: / size: 51G used: 22G (47%) fs: ext4 dev: /dev/sda2
           label: N/A uuid: 2a458a64-a8e0-4047-842a-e00a28b4afd7
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 31.0C mobo: N/A gpu: 0.0:60C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 205 Uptime: 35 min Memory: 1364.5/3926.7MB
           Init: systemd v: 237 runlevel: 5 Gcc sys: 7.3.0 Client: Unknown : systemd inxi: 2.3.56
'
```

Any ideas?

---

### Post by slickymaster on 2019-01-03
*Thread moved to **Hardware**.*

---

### Post by Yellow Pasque on 2019-01-03
> I have tried adding & removing these and now seem to have completely messed up my sound settings.

If you did something and that made things worse, the logical response would be to undo it. If you need help with that, you need to be much more specific about what you did and what commands you ran (giving links if you do not know how to explain). What did you add and remove? Packages? Which ones?

See if you can get more detailed information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> I thought the NVidia card was graphics only?

It has a built-in audio codec to send sound through HDMI/Displayport. There are ways to disable it, but you shouldn't have to.

---

### Post by Timothy Taylor on 2019-01-04
All sorted.  It was my BIOS battery failing, triggering default settings to be loaded with on-board sound enabled.  I've replaced the battery, done a fresh install and everything's working nicely.  Thanks for replies.

---

