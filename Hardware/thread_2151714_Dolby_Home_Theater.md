---
title: "Dolby Home Theater"
date: 2013-06-05
forum: Hardware
---

### Post by batelje on 2013-06-05
Hi everyone ! 

I stepped from windows 8 to ubuntu couple of weeks ago. I was a fan before but the 12.x versions were to buggy for my laptop (no sound, random freezes...)
I tryed 13.04 again and wow, amazing !

However...

There is 1 thing I miss in ubuntu that I could achieve on windows 8 ; The use of dolby home theater. Amazing software, with 1 click on the ON button my sound improved a lot! Even without using the equalizer-settings that came with it.
Is there any way to achieve this on Ubuntu ? tryed pulseaudio-equalizer but the sound does not even come close to dolby home theater.

I searched google but can't find any solutions, and most of the posts that say anything about Dolby for Linux are to complicated for an average user like me...

Some info about my sound :

```
tom@tom-Aspire-5830TG:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20588 Analog [CX20588 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: CX20588 Digital [CX20588 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

[IMG]http://oi39.tinypic.com/6j22py.jpg[/IMG]

```
tom@tom-Aspire-5830TG:~$ pacmd list-sinks
Welcome to PulseAudio! Use "help" for usage information.
>>> 1 sink(s) available.
  * index: 8
	name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9959
	volume: 0:  44% 1:  37%
	        0: -21.65 dB 1: -26.11 dB
	        balance -0.16
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max request: 0 KiB
	max rewind: 0 KiB
	monitor source: 11
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
	card: 0 <alsa_card.pci-0000_00_1b.0>
	module: 4
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "CX20588 Analog"
		alsa.id = "CX20588 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel PCH"
		alsa.long_card_name = "HDA Intel PCH at 0xd1c00000 irq 52"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.name = "6 Series/C200 Series Chipset Family High Definition Audio Controller"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Built-in Audio Analog Stereo"
		alsa.mixer_name = "Intel CougarPoint HDMI"
		alsa.components = "HDA:14f1506c,1025055b,00100002 HDA:80862805,80860101,00100000"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
			properties:
				device.icon_name = "audio-speakers"
		analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-headphones"
	active port: <analog-output-speaker>
```

OH! almost forgot : 
tom@tom-Aspire-5830TG:~$ alsamixer
cannot open mixer: No such file or directory

Pavucontrol works fine

---

### Post by mehmethakan on 2014-01-07
Same problem here, Acer Aspire V3-772G.
Thanks for replies!

---

