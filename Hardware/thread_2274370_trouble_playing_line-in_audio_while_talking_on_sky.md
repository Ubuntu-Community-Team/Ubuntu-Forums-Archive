---
title: "trouble playing line-in audio while talking on skype."
date: 2015-04-19
forum: Hardware
---

### Post by tcll5850 on 2015-04-19
this is something I've been dealing with for a while and askubuntu has gotten me nowhere for the past 2 months or so...

basically, I can only have 1 audio input source, and that's either line in or mic in, I can't use both for some reason.

also, when selecting line in, I have to enable loopback or I won't hear anything.
when selecting mic in, I have to disable loopback for obvious reasons.

how can I make it to where I can talk with my friends while playing whatever through my line in??

---

### Post by tcll5850 on 2015-04-20
screw it
since nobody has been able to help me for months

where can I contact the developers of Pulse Audio??

---

### Post by tcll5850 on 2015-04-21
ok, I just did some research and found out alsa was better, but skype uses pulse with no option to select alsa...

alsa however allows audio input from input source 1, pulse does not.

how can I configure loopback to use input source 1 instead of the primary input source??

---

### Post by tcll5850 on 2015-04-21
well, after countless google searches, I'm still getting nowhere... 
apparently playing a console game though your compy's speaker system while talking to a friend through your compy's mic seems to be a bit unheard of.

so here's another approach:
[img]http://lh3.ggpht.com/-xno-6s0GfyI/VTb0xG4UnzI/AAAAAAAAI5w/8C1KwRjdcO8/s715/alsa.png[/img]

[color=gray]Input Source[/color] is already used by skype through pulse and works perfectly
[color=red]<Input Source 1>[/color] is now configured for my WiiU (or MP3 player), though you currently can't hear anything.

how can I enable loopback output of Input Source 1??

EDIT:
for more info, here's what pulse reports:
```
$ pacmd list-sources
Welcome to PulseAudio! Use "help" for usage information.
>>> 2 source(s) available.
    index: 0
	name: <alsa_output.pci-0000_00_05.0.analog-stereo.monitor>
	driver: <module-alsa-card.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 1950
	volume: 0:  20% 1:  20%
	        0: -41.99 dB 1: -41.99 dB
	        balance 0.00
	base volume: 100%
	             0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 36.00 .. 371.52 ms
	monitor_of: 0
	card: 0 <alsa_card.pci-0000_00_05.0>
	module: 5
	properties:
		device.description = "Monitor of Built-in Audio Analog Stereo"
		device.class = "monitor"
		alsa.card = "0"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xfadf8000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:05.0"
		sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.id = "03f0"
		device.product.name = "MCP61 High Definition Audio"
		device.form_factor = "internal"
		device.string = "0"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
  * index: 1
	name: <alsa_input.pci-0000_00_05.0.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9959
	volume: 0:  29% 1:  29%
	        0: -32.52 dB 1: -32.52 dB
	        balance 0.00
	base volume:   9%
	             -63.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 0 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 36.00 .. 371.52 ms
	card: 0 <alsa_card.pci-0000_00_05.0>
	module: 5
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC662 rev1 Analog"
		alsa.id = "ALC662 rev1 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA NVidia"
		alsa.long_card_name = "HDA NVidia at 0xfadf8000 irq 22"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:05.0"
		sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "10de"
		device.vendor.name = "NVIDIA Corporation"
		device.product.id = "03f0"
		device.product.name = "MCP61 High Definition Audio"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Built-in Audio Analog Stereo"
		alsa.mixer_name = "Realtek ALC662 rev1"
		alsa.components = "HDA:10ec0662,103c2a99,00100101"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		analog-input-microphone-front: Front Microphone (priority 8500, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-input-microphone"
		analog-input-microphone-rear: Rear Microphone (priority 8200, latency offset 0 usec, available: yes)
			properties:
				device.icon_name = "audio-input-microphone"
		analog-input-linein: Line In (priority 8100, latency offset 0 usec, available: yes)
			properties:
				
	active port: <analog-input-microphone-rear>
```

---

### Post by tcll5850 on 2015-04-23
bump

nobody knows anything about alsa to help??

---

### Post by tcll5850 on 2015-05-03
so I'm guessing this isn't possible...

anyone know of anything better??

---

### Post by tcll5850 on 2015-05-17
so who's the dumb who designed this very limited interface:
[img]http://lh3.ggpht.com/-4NHKzMr-Bl8/VViy25_7mBI/AAAAAAAAJJA/9MbY7l2xOsg/s666/Screenshot%252520-%25252005172015%252520-%25252011%25253A23%25253A08%252520AM.png[/img]

why can't I select both my line and mic and enable loopback on my line (not my mic)??

more detailed info here:
[https://forum.xfce.org/viewtopic.php?pid=37527#p37527](https://forum.xfce.org/viewtopic.php?pid=37527#p37527)

---

