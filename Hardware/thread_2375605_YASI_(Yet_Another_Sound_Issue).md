---
title: "YASI? (Yet Another Sound Issue)"
date: 2017-10-25
forum: Hardware
---

### Post by dvlchd3 on 2017-10-25
I just purchased Origin PCs EVO 15-S and attempted to get Ubuntu Budgie 17.10 installed.  Everything is working awesome, except the freaking built-in sound (speakers or headphone jack).  HDMI sound seems to work after installing the Nvidia drivers, bit I rarely have an external monitor plugged in.

I have poked around a bit in different (outdated?) articles diagnosing sound issues to no avail.  Looking at `pavucontrol` I can see the output levels are moving (as if pulse thinks it's pushing out sound) and everything appears unmuted in `alsamixer`, but nothing comes out of the speakers or headphones (if I plug them in).

I'm assuming (hoping) this is a sound configuration issue, but have zero idea how to go about experimenting with what seem like endless suggestions to changing pulse/alsa configs.  I don't mind educated guessing and testing, but at this point I'm just guessing, so any help would be greatly appreciated!

Here's some output of things:

```

dan@LINE:~$ pacmd
Welcome to PulseAudio 10.0! Use "help" for usage information.
>>> list-sinks
1 sink(s) available.
  * index: 0
	name: <alsa_output.pci-0000_00_1f.3.analog-stereo>
	driver: <module-alsa-card.c>
	flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: SUSPENDED
	suspend cause: IDLE 
	priority: 9959
	volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
	        balance 0.00
	base volume: 65536 / 100% / 0.00 dB
	volume steps: 65537
	muted: no
	current latency: 0.00 ms
	max request: 0 KiB
	max rewind: 0 KiB
	monitor source: 0
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 0
	linked by: 0
	configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
	card: 1 <alsa_card.pci-0000_00_1f.3>
	module: 7
	properties:
		alsa.resolution_bits = "16"
		device.api = "alsa"
		device.class = "sound"
		alsa.class = "generic"
		alsa.subclass = "generic-mix"
		alsa.name = "ALC1220 Analog"
		alsa.id = "ALC1220 Analog"
		alsa.subdevice = "0"
		alsa.subdevice_name = "subdevice #0"
		alsa.device = "0"
		alsa.card = "0"
		alsa.card_name = "HDA Intel PCH"
		alsa.long_card_name = "HDA Intel PCH at 0xdf620000 irq 145"
		alsa.driver_name = "snd_hda_intel"
		device.bus_path = "pci-0000:00:1f.3"
		sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
		device.bus = "pci"
		device.vendor.id = "8086"
		device.vendor.name = "Intel Corporation"
		device.product.id = "a171"
		device.form_factor = "internal"
		device.string = "front:0"
		device.buffering.buffer_size = "65536"
		device.buffering.fragment_size = "32768"
		device.access_mode = "mmap+timer"
		device.profile.name = "analog-stereo"
		device.profile.description = "Analog Stereo"
		device.description = "Built-in Audio Analog Stereo"
		alsa.mixer_name = "Realtek ALC1220"
		alsa.components = "HDA:10ec1220,15589501,00100003 HDA:8086280b,80860101,00100000"
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
>>> 

```

```

dan@LINE:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC1220 Analog [ALC1220 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1220 Digital [ALC1220 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

dan@LINE:~$ lspci -v | grep -A7 -i "audio"
00:1f.3 Audio device: Intel Corporation Device a171 (rev 31)
	Subsystem: CLEVO/KAPOK Computer Device 9501
	Flags: bus master, fast devsel, latency 32, IRQ 145
	Memory at df620000 (64-bit, non-prefetchable) [size=16K]
	Memory at df600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
--
01:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)
	Subsystem: Intel Corporation GP104 High Definition Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at df080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

03:00.0 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5250 PCI Express Card Reader (rev 01) (prog-if 01)

```

```

dan@LINE:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/4.13.0-16-generic/kernel/sound/synth/snd-util-mem.ko
/lib/modules/4.13.0-16-generic/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/4.13.0-16-generic/kernel/sound/x86/snd-hdmi-lpe-audio.ko
/lib/modules/4.13.0-16-generic/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/xtensa/snd-soc-xtfpga-i2s.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/fsl/snd-soc-fsl-ssi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/fsl/snd-soc-imx-audmux.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/fsl/snd-soc-fsl-esai.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/fsl/snd-soc-fsl-asrc.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/fsl/snd-soc-fsl-sai.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/fsl/snd-soc-fsl-spdif.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/generic/snd-soc-simple-card-utils.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/generic/snd-soc-simple-card.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-skl_nau88l25_max98357a.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-kbl_rt5663_rt5514_max98927.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bdw-rt5677-mach.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-rt5645.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-rt5672.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-byt-cht-da7213.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-kbl_rt5663_max98927.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-byt-cht-es8316.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-max98090_ti.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-skl_nau88l25_ssm4567.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bxt-rt298.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bytcr-rt5640.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-haswell.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-skl_rt286.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-broadwell.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-byt-cht-nocodec.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bxt-da7219_max98357a.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/boards/snd-soc-sst-bytcr-rt5651.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/atom/snd-soc-sst-atom-hifi2-platform.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/atom/sst/snd-intel-sst-core.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/atom/sst/snd-intel-sst-acpi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/skylake/snd-soc-skl-ipc.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/skylake/snd-soc-skl.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/haswell/snd-soc-sst-haswell-pcm.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/common/snd-soc-sst-firmware.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/common/snd-soc-sst-ipc.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/common/snd-soc-sst-acpi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/common/snd-soc-sst-match.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/intel/common/snd-soc-sst-dsp.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/amd/snd-soc-acp-pcm.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-pcm512x.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tas2552.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt5677-spi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-sigmadsp.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-adau-utils.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ssm4567.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rl6347a.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-pcm179x-codec.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs42l56.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs4271-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs42l42.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-pcm512x-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-sta32x.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-sigmadsp-regmap.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt5670.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt5514.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic31xx.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-adau1761-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-max98927.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-da7213.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-spdif-rx.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tfa9879.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8804-spi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs53l30.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-sigmadsp-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs42l52.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ssm2602-spi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-nau8824.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-inno-rk3036.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs4271-spi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-pcm179x-spi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-pcm3168a-spi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs42xx8-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-nau8540.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ts3a227e.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-adau1701.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-pcm3168a.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs42l51-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-sti-sas.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-bt-sco.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-pcm1681.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ak4554.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-nau8810.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs4349.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ak5386.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-msm8916-analog.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-hdac-hdmi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-adau17x1.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ac97.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-es8316.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-pcm3168a-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt5677.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt298.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-adau1761.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt5640.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-pcm512x-spi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt5645.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs35l32.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt5616.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-si476x.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-da7219.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tas571x.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-spdif-tx.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-gtm601.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-dmic.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-max9860.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rl6231.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-es8328-spi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs42xx8.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt5663.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8985.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs4265.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-max98357a.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-hdmi-codec.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs35l34.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tas5720.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-dio2125.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-adau1761-spi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tas5086.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-adau7002.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-nau8825.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic23-spi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt5651.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs35l33.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-zx-aud96p22.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-sta350.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-max98090.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ak4613.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt286.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-msm8916-digital.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs42l73.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-max98504.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-es8328-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-es7134.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-es8328.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-cs35l35.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-pcm179x-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-wm8804-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/codecs/snd-soc-ssm2602-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/soc/snd-soc-core.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/seq/snd-seq.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/snd-hwdep.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/snd-rawmidi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/snd-seq-device.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/snd-timer.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/snd-pcm.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/snd-hrtimer.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/snd.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/snd-pcm-dmaengine.ko
/lib/modules/4.13.0-16-generic/kernel/sound/core/snd-compress.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-bt87x.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-ens1371.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-ad1889.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-ens1370.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-via82xx.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-es1938.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-als300.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-cmipci.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-maestro3.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-rme96.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-rme32.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-fm801.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-es1968.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-als4000.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-cs4281.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-generic.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pci/snd-azt3328.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/snd-mts64.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/snd-aloop.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/snd-dummy.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/4.13.0-16-generic/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/4.13.0-16-generic/kernel/sound/i2c/snd-i2c.ko
/lib/modules/4.13.0-16-generic/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/4.13.0-16-generic/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/4.13.0-16-generic/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/4.13.0-16-generic/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/4.13.0-16-generic/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/4.13.0-16-generic/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/hiface/snd-usb-hiface.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/bcd2000/snd-bcd2000.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/line6/snd-usb-line6.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/line6/snd-usb-toneport.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/line6/snd-usb-pod.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/line6/snd-usb-podhd.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/line6/snd-usb-variax.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/4.13.0-16-generic/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/4.13.0-16-generic/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/4.13.0-16-generic/kernel/sound/firewire/motu/snd-firewire-motu.ko
/lib/modules/4.13.0-16-generic/kernel/sound/firewire/bebob/snd-bebob.ko
/lib/modules/4.13.0-16-generic/kernel/sound/firewire/digi00x/snd-firewire-digi00x.ko
/lib/modules/4.13.0-16-generic/kernel/sound/firewire/dice/snd-dice.ko
/lib/modules/4.13.0-16-generic/kernel/sound/firewire/tascam/snd-firewire-tascam.ko
/lib/modules/4.13.0-16-generic/kernel/sound/firewire/snd-isight.ko
/lib/modules/4.13.0-16-generic/kernel/sound/firewire/fireworks/snd-fireworks.ko
/lib/modules/4.13.0-16-generic/kernel/sound/firewire/oxfw/snd-oxfw.ko
/lib/modules/4.13.0-16-generic/kernel/sound/firewire/fireface/snd-fireface.ko
/lib/modules/4.13.0-16-generic/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/4.13.0-16-generic/kernel/sound/hda/snd-hda-core.ko
/lib/modules/4.13.0-16-generic/kernel/sound/hda/ext/snd-hda-ext-core.ko
/lib/modules/4.13.0-16-generic/updates/dkms/snd-hda-codec-ca0110.ko
/lib/modules/4.13.0-16-generic/updates/dkms/snd-hda-codec.ko
/lib/modules/4.13.0-16-generic/updates/dkms/snd-hda-codec-idt.ko
/lib/modules/4.13.0-16-generic/updates/dkms/snd-hda-codec-generic.ko
/lib/modules/4.13.0-16-generic/updates/dkms/snd-hda-codec-hdmi.ko
/lib/modules/4.13.0-16-generic/updates/dkms/snd-hda-intel.ko
/lib/modules/4.13.0-16-generic/updates/dkms/snd-hda-ext-core.ko
/lib/modules/4.13.0-16-generic/updates/dkms/snd-hda-codec-ca0132.ko

```

---

