---
title: "This sound device does not have any controls"
date: 2011-09-05
forum: Hardware
---

### Post by omlx2 on 2011-09-05
hi to all>>>
i have sound problem ,,,the sound suddenly stop>>
i tried to solve it but i couldn't
am using 11.04


aplay -l
 **** List of PLAYBACK Hardware Devices ****
  
~$ alsamixer
 This sound device does not have any controls
~$  cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xb0000000 irq 43

and
 sudo lspci -v

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Lenovo Device 2066
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel




:~$ cat /proc/asound/versionAdvanced Linux Sound Architecture Driver Version 1.0.23.


[http://www.alsa-project.org/db/?f=b4da7d90732586ec09abe590ab117101fd607b4f](http://www.alsa-project.org/db/?f=b4da7d90732586ec09abe590ab117101fd607b4f)

---

