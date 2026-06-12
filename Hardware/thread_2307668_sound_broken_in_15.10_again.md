---
title: "sound broken in 15.10 again"
date: 2015-12-27
forum: Hardware
---

### Post by pickarooney on 2015-12-27
I had to do a fresh reinstall of Wily last night and everything was running OK until I decided to install gstreamer1.0 (I was trying to make HEVC codecs work and this somehow got involved).
I have no sound whatsoever, although all my multimedia applications act as though they are playing away with no problem.

My sound card is an onboard ATI SB and it shows OK in lspci

```
 lspci -v | grep -A7 -i "audio"
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 840c
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fcff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
--
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8334
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fea7c000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel

```

Likewise, aplay lists it

```

udo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: VT1708S Alt Analog [VT1708S Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 3: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The volume level is at 100% in both alsamixer and the audio widget on the xfce panel.

In the audio settings I only have one entry, though, the HDMI connection (See screenshot).

Any ideas? I've tried rebooting...

---

