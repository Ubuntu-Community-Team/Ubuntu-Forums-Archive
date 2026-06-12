---
title: "No Microphone: HP EliteBook 840 G6, Ubuntu 19.10"
date: 2020-02-24
forum: Hardware
---

### Post by datakid on 2020-02-24
As noted in title, the [Bang and Olfsun audio]("https://support.hp.com/us-en/product/hp-elitebook-840-g6-notebook-pc/26609796/document/c06352019#AbT8") is very fancy but it doesn't have drivers. Audio works fine, it's the microphone that isn't even recognised.

lspci -v:
```

00:1f.3 Multimedia audio controller: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 11)
	Subsystem: Hewlett-Packard Company Cannon Point-LP High Definition Audio Controller
	Flags: bus master, fast devsel, latency 64, IRQ 185
	Memory at 4022108000 (64-bit, non-prefetchable) [size=16K]
	Memory at 4022000000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel, snd_soc_skl, sof_pci_dev

```

```

$ cat /proc/asound/card0/pcm0c/info
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC215 Analog
name: ALC215 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

```

```

$ lsmod | grep snd
snd_hda_codec_hdmi     61440  1
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
snd_sof_intel_hda_common    73728  1 sof_pci_dev
snd_sof_intel_hda      20480  1 snd_sof_intel_hda_common
snd_sof_intel_byt      24576  1 sof_pci_dev
snd_sof_intel_ipc      20480  1 snd_sof_intel_byt
snd_sof               102400  4 snd_sof_intel_hda_common,snd_sof_intel_byt,snd_sof_intel_ipc,sof_pci_dev
snd_sof_xtensa_dsp     16384  1 sof_pci_dev
snd_soc_skl           106496  0
snd_soc_hdac_hda       24576  2 snd_sof_intel_hda_common,snd_soc_skl
snd_hda_ext_core       32768  4 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl,snd_sof_intel_hda
snd_soc_skl_ipc        65536  1 snd_soc_skl
snd_soc_sst_ipc        20480  1 snd_soc_skl_ipc
snd_soc_sst_dsp        36864  1 snd_soc_skl_ipc
snd_soc_acpi_intel_match    28672  3 snd_sof_intel_hda_common,sof_pci_dev,snd_soc_skl
snd_soc_acpi           16384  3 snd_soc_acpi_intel_match,sof_pci_dev,snd_soc_skl
snd_soc_core          241664  4 snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl
snd_compress           24576  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          49152  2
snd_hda_codec         131072  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda
snd_hda_core           90112  10 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl,snd_sof_intel_hda
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  10 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_sof,snd_sof_intel_hda_common,snd_soc_core,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
snd                    90112  17 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
soundcore              16384  1 snd

```

Fully up to date 19.10, kernel is 5.3.0-40-generic. Similar to [this problem]("https://askubuntu.com/questions/1189478/microphone-not-detected-ubuntu-19-10-laptop-hp-envy-13-sound-device-realtek") but different model laptop.

---

### Post by pablomos on 2020-03-11
I'm having the exact same problem. My computer is Elitebook 830 G6, which is very similar to the one posted in this thread. I've tried editing /etc/modprobe.d/alsa-base.conf with this line:
options snd-hda-intel model=hp
but had no luck

---

### Post by mörgæs on 2020-03-11
With hardware as new as this 19.10 may not even be fresh enough. You could try a live boot of 20.04 though it's still in development.

---

