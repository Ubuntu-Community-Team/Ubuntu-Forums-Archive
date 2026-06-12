---
title: "Toshiba A205 S-4587 microphone issue"
date: 2009-11-06
forum: Hardware
---

### Post by bibloks on 2009-11-06
Greetings, 

Prior to this post I have read plenty posts related microphone issue but could not fix here (plugging headphone with mic. will work but mike sound is bad quality) 

Check what's outcome bellow and if you could guide me what to do to make it work. Ubuntu 9.10 installed.

I have installed latest drivers for realtek from official site and sound is working but mike is not!

Thanks allot 


> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

 

 > lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


> cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC268
Codec: LSI ID 1040

---

