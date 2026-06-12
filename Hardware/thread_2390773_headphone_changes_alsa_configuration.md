---
title: "headphone changes alsa configuration"
date: 2018-05-02
forum: Hardware
---

### Post by dd34342 on 2018-05-02
Hello

After reinstalling my PC with 18.04 (from 16.04) I noticed that the sound didn't restore itself to go through my analog output after using my headphones.
It seems to change alsa.  The only way I found (so far) to restore it is to reboot.

Before using headphones:
pacmd list-sinks
1 sink(s) available.
  * index: 0
	name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9039
	volume: front-left: 9116 /  14% / -51,40 dB,   front-right: 9116 /  14% / -51,40 dB
	        balance 0,00
	base volume: 65536 / 100% / 0,00 dB
	volume steps: 65537
	muted: no
	current latency: 0,00 ms
	max request: 0 KiB
	max rewind: 0 KiB
	monitor source: 0
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0,00 ms; range is 0,50 .. 371,52 ms
	card: 1 <alsa_card.pci-0000_00_1b.0>
	module: 8
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC892 Analog"
		alsa.id = "ALC892 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel PCH"
		alsa.long_card_name = "HDA Intel PCH at 0xfbf20000 irq 57"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "1d20"
		device.product.name = "C600/X79 series chipset High Definition Audio Controller"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Built-in Audio Analog Stereo"
		alsa.mixer_name = "Realtek ALC892"
		alsa.components = "HDA:10ec0892,10438436,00100302"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		analog-output-lineout: Line Out (priority 9900, latency offset 0 usec, available: no)
			properties:
				
		analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
			properties:
				device.icon_name = "audio-headphones"
	active port: <analog-output-lineout>




After using headphones 
1 sink(s) available.
  * index: 2
	name: <alsa_output.pci-0000_00_1b.0.iec958-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9038
	volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB
	        balance 0,00
	base volume: 65536 / 100% / 0,00 dB
	volume steps: 65537
	muted: no
	current latency: 0,00 ms
	max request: 0 KiB
	max rewind: 0 KiB
	monitor source: 4
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0,00 ms; range is 0,50 .. 371,52 ms
	card: 1 <alsa_card.pci-0000_00_1b.0>
	module: 8
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC892 Digital"
		alsa.id = "ALC892 Digital"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "1"
		alsa.card = "0"
		alsa.card_name = "HDA Intel PCH"
		alsa.long_card_name = "HDA Intel PCH at 0xfbf20000 irq 57"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1b.0"
		sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "1d20"
		device.product.name = "C600/X79 series chipset High Definition Audio Controller"
		device.form_factor = "internal"
		device.string = "iec958:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "iec958-stereo"
		device.profile.description = "Digital Stereo (IEC958)"
		device.description = "Built-in Audio Digital Stereo (IEC958)"
		alsa.mixer_name = "Realtek ALC892"
		alsa.components = "HDA:10ec0892,10438436,00100302"
		module-udev-detect.discovered = "1"
		device.icon_name = "audio-card-pci"
	ports:
		iec958-stereo-output: Digital Output (S/PDIF) (priority 0, latency offset 0 usec, available: unknown)
			properties:
				
	active port: <iec958-stereo-output>

---

### Post by dd34342 on 2018-05-02
"killall pulseaudio" also restores the alsa and 'reactivates' the analog output.  I can live with this.

---

### Post by 13787110225-p on 2018-05-10
the same case

---

