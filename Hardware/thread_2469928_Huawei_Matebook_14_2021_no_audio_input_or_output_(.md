---
title: "Huawei Matebook 14 2021 no audio input or output ('Dummy Output')"
date: 2021-12-13
forum: Hardware
---

### Post by ambarry on 2021-12-13
I have a Matebook 14 (2021 version - i7, 16GB ram).  On Windows it's audio works fine.  On Ubuntu 20.04 (and 21.10 and Fedora latest) the internal speakers and microphone are not picked up and 'Dummy Output' is the only audio selection in Settings.  Interestingly, audio over Bluetooth works fine.

Here is the info you need to know about devices etc:
> sudo inxi -A
Audio:
  Device-1: Intel driver: sof-audio-pci 
  Sound Server: ALSA v: k5.11.0-41-generic 

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: sofhdadsp [sof-hda-dsp], device 1: HDMI1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 2: HDMI2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 3: HDMI3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> pacmd list-sources
1 source(s) available.
  * index: 2
	name: <auto_null.monitor>
	driver: <module-null-sink.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE
	priority: 1000
	volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
	        balance 0.00
	base volume: 65536 / 100% / 0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max rewind: 344 KiB
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
	monitor_of: 2
	module: 30
	properties:
		device.description = "Monitor of Dummy Output"
		device.class = "monitor"
		device.icon_name = "audio-input-microphone"

> pacmd list-sinks
1 sink(s) available.
  * index: 2
	name: <auto_null>
	driver: <module-null-sink.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE
	priority: 1000
	volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
	        balance 0.00
	base volume: 65536 / 100% / 0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max request: 344 KiB
	max rewind: 344 KiB
	monitor source: 2
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
	module: 30
	properties:
		device.description = "Dummy Output"
		device.class = "abstract"
		device.icon_name = "audio-card"

> lspci
...
00:1f.3 Multimedia audio controller: Intel Corporation Device a0c8 (rev 20)
...


So, the audio hardware is seen (Intel multimedia audio controller), the right driver is in use (sof-audio-pci) but no speakers or microphone are detected for PulseAudio to use.

Any suggestions? Already reinstalled alsabase and PulseAudio and force-reloaded, and checked nothing is simply muted using pavucontrol (which shows no cards available to configure).  I don't have Timidity installed and so the known issues with Timidity Daemon aren't a factor.

Seems rather that the driver isn't correctly configured for the hardware in the laptop ... but how to find and give the right config??

Any help greatly appreciated!

Thanks.

---

### Post by ambarry on 2021-12-13
Additional diagnostics:

> dmesg | egrep -i "(sof|snd)"  (cut down to only the relevant lines):

[    2.646578] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    2.646602] snd_hda_intel 0000:00:1f.3: Digital mics found on Skylake+ platform, using SOF driver
[    2.665021] sof-audio-pci 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    2.665042] sof-audio-pci 0000:00:1f.3: Digital mics found on Skylake+ platform, using SOF driver
[    2.665055] sof-audio-pci 0000:00:1f.3: enabling device (0000 -> 0002)
[    2.665268] sof-audio-pci 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040100
[    3.596999] sof-audio-pci 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.664478] sof-audio-pci 0000:00:1f.3: use msi interrupt mode
[    3.676750] sof-audio-pci 0000:00:1f.3: hda codecs found, mask 4
[    3.676753] sof-audio-pci 0000:00:1f.3: using HDA machine driver skl_hda_dsp_generic now
[    3.676759] sof-audio-pci 0000:00:1f.3: DMICs detected in NHLT tables: 4
[    3.779611] sof-audio-pci 0000:00:1f.3: Firmware info: version 1:6:0-18fab
[    3.779614] sof-audio-pci 0000:00:1f.3: Firmware: ABI 3:17:0 Kernel ABI 3:18:0
[    3.785619] sof-audio-pci 0000:00:1f.3: Topology: ABI 3:17:0 Kernel ABI 3:18:0
[    3.792845] sof-audio-pci 0000:00:1f.3: ASoC: Parent card not yet available, widget card binding deferred

---

### Post by ambarry on 2021-12-14
Update - I upgraded from 20.04 to 21.10, but still no sound!

Changes:

> sudo inxi -A
Audio:     Device-1: Intel Tiger Lake-LP Smart Sound Audio driver: sof-audio-pci-intel-tgl 
           Sound Server-1: ALSA v: k5.13.0-22-generic running: yes 
           Sound Server-2: PulseAudio v: 15.0 running: yes 
           Sound Server-3: PipeWire v: 0.3.32 running: yes

> sudo dmesg | egrep -i "(sof|snd)" (cut down to only the relevant lines):

[    2.551763] snd_hda_intel 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    2.551798] snd_hda_intel 0000:00:1f.3: Digital mics found on Skylake+ platform, using SOF driver
[    2.672344] sof-audio-pci-intel-tgl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    2.672363] sof-audio-pci-intel-tgl 0000:00:1f.3: Digital mics found on Skylake+ platform, using SOF driver
[    2.672378] sof-audio-pci-intel-tgl 0000:00:1f.3: enabling device (0000 -> 0002)
[    2.672573] sof-audio-pci-intel-tgl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040100
[    3.578031] sof-audio-pci-intel-tgl 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    3.654522] sof-audio-pci-intel-tgl 0000:00:1f.3: use msi interrupt mode
[    3.676049] sof-audio-pci-intel-tgl 0000:00:1f.3: hda codecs found, mask 4
[    3.676054] sof-audio-pci-intel-tgl 0000:00:1f.3: using HDA machine driver skl_hda_dsp_generic now
[    3.676057] sof-audio-pci-intel-tgl 0000:00:1f.3: DMICs detected in NHLT tables: 4
[    3.778088] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware info: version 1:6:0-18fab
[    3.778092] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware: ABI 3:17:0 Kernel ABI 3:18:0
[    3.784202] sof-audio-pci-intel-tgl 0000:00:1f.3: Topology: ABI 3:17:0 Kernel ABI 3:18:0
[    3.791769] sof-audio-pci-intel-tgl 0000:00:1f.3: ASoC: Parent card not yet available, widget card binding deferred
[    3.819988] input: sof-hda-dsp HDMI/DP,pcm=1 as /devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0/input20
[    3.820046] input: sof-hda-dsp HDMI/DP,pcm=2 as /devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0/input21
[    3.820087] input: sof-hda-dsp HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0/input22

---

### Post by ambarry on 2022-05-13
Sadly, still no sound on Ubuntu 22.04.  The output of inxi is identical, and of dmesg grepping for sod|snd is only changed in these lines:

[    2.829012] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware info: version 2:0:0-b678a
[    2.829017] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware: ABI 3:20:0 Kernel ABI 3:18:0
[    2.829020] sof-audio-pci-intel-tgl 0000:00:1f.3: warn: FW ABI is more recent than kernel
[    2.829025] sof-audio-pci-intel-tgl 0000:00:1f.3: unknown sof_ext_man header type 3 size 0x30
[    2.923961] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware info: version 2:0:0-b678a
[    2.923968] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware: ABI 3:20:0 Kernel ABI 3:18:0
[    2.923972] sof-audio-pci-intel-tgl 0000:00:1f.3: warn: FW ABI is more recent than kernel
[    3.060678] sof-audio-pci-intel-tgl 0000:00:1f.3: Topology: ABI 3:20:0 Kernel ABI 3:18:0
[    3.060690] sof-audio-pci-intel-tgl 0000:00:1f.3: warn: topology ABI is more recent than kernel

All other output is the same or very close to that given above.

PLEASE ... what is the problem??  It's a year old laptop now, but still no sound, nor any reply to this request.

---

### Post by cihatertem on 2022-05-27
> **ambarry said:**
> Sadly, still no sound on Ubuntu 22.04.  The output of inxi is identical, and of dmesg grepping for sod|snd is only changed in these lines:

[    2.829012] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware info: version 2:0:0-b678a
[    2.829017] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware: ABI 3:20:0 Kernel ABI 3:18:0
[    2.829020] sof-audio-pci-intel-tgl 0000:00:1f.3: warn: FW ABI is more recent than kernel
[    2.829025] sof-audio-pci-intel-tgl 0000:00:1f.3: unknown sof_ext_man header type 3 size 0x30
[    2.923961] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware info: version 2:0:0-b678a
[    2.923968] sof-audio-pci-intel-tgl 0000:00:1f.3: Firmware: ABI 3:20:0 Kernel ABI 3:18:0
[    2.923972] sof-audio-pci-intel-tgl 0000:00:1f.3: warn: FW ABI is more recent than kernel
[    3.060678] sof-audio-pci-intel-tgl 0000:00:1f.3: Topology: ABI 3:20:0 Kernel ABI 3:18:0
[    3.060690] sof-audio-pci-intel-tgl 0000:00:1f.3: warn: topology ABI is more recent than kernel

All other output is the same or very close to that given above.

PLEASE ... what is the problem??  It's a year old laptop now, but still no sound, nor any reply to this request.
Did you upgrade from pre-version or clean install for 22.04?

---

