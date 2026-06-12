---
title: "Sound not working on 16.04 LTS"
date: 2017-05-08
forum: Hardware
---

### Post by mclaren2 on 2017-05-08
First of all, some info:
Card: HDA ATI SB
Chip: Realtek ALC887-VD
Kernel: 4.8.0-51-generic
Ubuntu Version: 16.04 LTS



```
sudo lspci -v

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
    Subsystem: Gigabyte Technology Co., Ltd SBx00 Azalia (Intel HDA)
    Flags: bus master, slow devsel, latency 32, IRQ 3
    Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel modules: snd_hda_intel

01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd GK208 HDMI/DP Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel modules: snd_hda_intel



```

```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Yes, I have done alsamixer, and:
[LIST]
[*]Unmuted all channels [Master, Headphone, PCM, Front, Surround, Center, LFE] and set them to 100.
[/LIST]

---

### Post by mclaren2 on 2017-05-08
OK, I went on the IRC and a guy helped me fix it. For anyone wanting the solution, here it is:

1. Go to terminal and enter pavucontrol.
2. Go to configuration, and:
3. Disable the HDMI output device, and then go back to output devices, and: 
4. Set the other device (the actual soundcard) as default and unmute it

---

### Post by RobGoss on 2017-05-08
Thanks for sharing your  solution with the forum, if you have resolved your issue you can mark this thread as solved, use the **Thread tool** tab at the top of this post

Have a great day

---

