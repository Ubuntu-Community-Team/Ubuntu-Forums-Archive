---
title: "Playback-problems with onboard SiS 7012/intel8x0 audio"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by Ensnared on 2006-04-10
Hello,

I've got some big problems with my SiS 7012 onboard audio-controller in Breezy. The computer is an EliteGroup G732 laptop with a SiS chipset, and the driver for this in alsa is apparently the intel8x0 driver.

The problem is the sound quality - that is, the times it plays anything at all. It is very choppy, distorted, and it skips a lot. Basically it's impossible to listen to anything at all. I've tried compiling a new kernel (2.6.12.2) but that didn't make any difference whatsoever.

I've tried fiddling with the period_size and buffer_size settings in /etc/asound.conf and this seems to make some difference in the chopping of the sound, but it doesn't seem like it's possible to make it work properly regardless of settings. My current asound.conf looks like this:```
pcm.card0 {
	type hw
	card 0
}

pcm.!default {
	type plug
	slave.pcm "dmixer"
}

pcm.dmixer {
	type dmix
	ipc_key 1025
	slave {
		pcm "hw:0,0"
		period_time 0
		period_size 1024
		buffer_size 8192
		rate 48000
	}
	bindings {
		0 0
		1 1
	}
}
```

'lsmod | grep snd' shows this:```
snd_intel8x0           31900  1
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            50080  0
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                83080  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              22660  1 snd_pcm
snd                    50432  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9440  1 snd
snd_page_alloc         10760  2 snd_intel8x0,snd_pcm
```

The lspci information for the sound controller is this:```

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
	Subsystem: Elitegroup Computer Systems: Unknown device b732
	Flags: bus master, medium devsel, latency 173, IRQ 23
	I/O ports at 1400 [size=256]
	I/O ports at 1080 [size=128]
	Capabilities: [48] Power Management version 2
```

Don't know if it matters, but 'lshw -C sound' gives this:```
  *-multimedia
       description: Multimedia audio controller
       product: Sound Controller
       vendor: Silicon Integrated Systems [SiS]
       physical id: 2.7
       bus info: pci@00:02.7
       version: a0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH
       resources: ioport:1400-14ff ioport:1080-10ff irq:23
```

Also, don't know if this matters, but this is the dmesg-output for the driver:```
[4294752.833000] intel8x0_measure_ac97_clock: measured 50236 usecs
[4294752.833000] intel8x0: measured clock 975 rejected
[4294752.833000] intel8x0: clocking to 48000
[4294753.511000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
```

I don't know if there's any other info that can be helpfull in tracking down the problem, but I really need some help here - google hasn't proven as helpfull as it usually does when I run into problems, and even though I've used Linux for a decade now I've never had this kind of problem before (don't get me started on the emu10k1-driver :P).

So - anyone able to help out with this? :)

---

