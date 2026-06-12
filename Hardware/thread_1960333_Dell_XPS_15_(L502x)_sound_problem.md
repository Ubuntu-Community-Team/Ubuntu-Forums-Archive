---
title: "Dell XPS 15 (L502x) sound problem"
date: 2012-04-17
forum: Hardware
---

### Post by coyoty on 2012-04-17
Hello, I have a problem with ubuntu 12.04 and 11.10, my laptop has a JBL 2.1 sound system and in ubuntu sound settings the bar for sub woofer is greyed out and the sub woofer does not work. Also the sound is really really bad compared to windows a lot of noise in the background. Is there any way to enable 2.1 sound on my laptop or to install another driver that will sound better ? The laptop uses a realtek high definition audio chipset.

---

### Post by zdavidlnx on 2012-04-29
> **coyoty said:**
> Hello, I have a problem with ubuntu 12.04 and 11.10, my laptop has a JBL 2.1 sound system and in ubuntu sound settings the bar for sub woofer is greyed out and the sub woofer does not work. Also the sound is really really bad compared to windows a lot of noise in the background. Is there any way to enable 2.1 sound on my laptop or to install another driver that will sound better ? The laptop uses a realtek high definition audio chipset.

I have the same problem. I always have noise in the background. Very Annoying.

I still have not found a solution ...

---

### Post by lauramolenaar on 2012-05-01
I have the same problem too. When I installed ubuntu 12.04 the sound became very noisy and not at all like the sound I had with Windows (7). This is my audio-controller:

```
laura@laura-XPS-L502X:~$ lspci -v | grep -A7 -i "audio" 
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: Dell Device 04b6
	Flags: bus master, fast devsel, latency 0, IRQ 51
	Memory at f1c00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

```

If you need any other information, just let me know!

---

### Post by machmaschneller on 2012-07-28
I have the same problem. The 2.1 JBL subwoofer doesn't work at all.

---

