---
title: "External Microphone not detected in Ubuntu 16.04"
date: 2017-05-08
forum: Hardware
---

### Post by icmv333 on 2017-05-08
Info on my system:

Distribution: Ubuntu 16.04
Kernel: 4.8.0-51-generic
Card: HDA Intel PCH
Chip: Realtek ALC255
Laptop: Acer E 14 E5-475G-30KY

```
$ lspci -nnk | grep -A2 Audio
00:1f.3 Audio device [0403]: Intel Corporation Sunrise Point-LP HD Audio [8086:9d70] (rev 21)
    Subsystem: Acer Incorporated [ALI] Sunrise Point-LP HD Audio [1025:110f]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl
```

```

$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC255 Analog [ALC255 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


I have a headset with a built-in microphone. Ubuntu detects the headset and uses it correctly but it does not detect the external microphone. I've tried using *hdajackretask* but it doesn't really help. All it does is rename my internal microphone. *linux-backports-modules-alsa-generic* results in a *unable to locate package* error. I'm dual-booting Windows 10 and my external microphone works perfectly there. I read that some people modified an alsa config file to fix their problem but I don't know if the lines they added would work in my system.


Edit: I tried the system check program on audio devices. It tested for both external, internal analog devices and internal, external usb devices. The internal microphone was receiving inputs even when test for external microphone and usb external microphone (even when no usb audio device was plugged in) were being conducted.

---

