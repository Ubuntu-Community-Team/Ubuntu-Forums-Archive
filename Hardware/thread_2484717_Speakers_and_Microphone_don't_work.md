---
title: "Speakers and Microphone don't work"
date: 2023-03-07
forum: Hardware
---

### Post by farob on 2023-03-07
Hi, today I installed Ubuntu (ver. 22.10) for the first time on a laptop with Intel CPU.
Microphone is not detected and the speakers don't make any sound even though there are no error messages. Connecting external headphones via jack there are no signs of life.
Would anyone know how to fix the problem? Thanks

---

### Post by #&amp;thj^% on 2023-03-07
please include your hardware, use this wrapped in code tags:
```
aplay --list-devices
```
and this:
```
/sbin/lsmod | grep snd

```
for Code Tags see my signature.

---

### Post by farob on 2023-03-08
Thanks for the reply, these are the outputs:
aplay --list-devices
```
**** List of PLAYBACK Hardware Devices ****card 0: sofessx8336 [sof-essx8336], device 0: ES8336 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofessx8336 [sof-essx8336], device 5: HDMI 1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofessx8336 [sof-essx8336], device 6: HDMI 2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofessx8336 [sof-essx8336], device 7: HDMI 3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

/sbin/lsmod | grep snd
```
snd_seq_dummy          16384  0
snd_hrtimer            16384  1
snd_soc_sof_es8336     20480  1
snd_soc_intel_hda_dsp_common    20480  1 snd_soc_sof_es8336
snd_sof_probes         20480  0
snd_hda_codec_hdmi     81920  1
snd_soc_dmic           16384  0
snd_sof_pci_intel_apl    16384  0
snd_sof_intel_hda_common   139264  1 snd_sof_pci_intel_apl
soundwire_intel        40960  1 snd_sof_intel_hda_common
snd_sof_intel_hda      20480  1 snd_sof_intel_hda_common
snd_sof_pci            24576  2 snd_sof_intel_hda_common,snd_sof_pci_intel_apl
snd_sof_xtensa_dsp     16384  1 snd_sof_intel_hda_common
snd_sof               208896  3 snd_sof_pci,snd_sof_intel_hda_common,snd_sof_probes
snd_sof_utils          20480  1 snd_sof
snd_soc_avs           131072  0
snd_soc_skl           176128  0
snd_soc_hdac_hda       24576  2 snd_sof_intel_hda_common,snd_soc_skl
snd_hda_ext_core       36864  5 snd_soc_avs,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl,snd_sof_intel_hda
snd_soc_sst_ipc        20480  1 snd_soc_skl
snd_soc_sst_dsp        36864  1 snd_soc_skl
snd_soc_acpi_intel_match    69632  3 snd_sof_intel_hda_common,snd_soc_skl,snd_sof_pci_intel_apl
snd_soc_acpi           16384  3 snd_soc_acpi_intel_match,snd_sof_intel_hda_common,snd_soc_skl
snd_hda_intel          53248  0
snd_intel_dspcfg       36864  4 snd_soc_avs,snd_hda_intel,snd_sof_intel_hda_common,snd_soc_skl
snd_intel_sdw_acpi     20480  2 snd_sof_intel_hda_common,snd_intel_dspcfg
snd_hda_codec         172032  5 snd_soc_avs,snd_hda_codec_hdmi,snd_hda_intel,snd_soc_intel_hda_dsp_common,snd_soc_hdac_hda
snd_hda_core          118784  10 snd_soc_avs,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_soc_intel_hda_dsp_common,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl,snd_sof_intel_hda
snd_hwdep              20480  1 snd_hda_codec
snd_soc_es8316         49152  1
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_soc_core          368640  10 snd_soc_avs,soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_sof_es8336,snd_soc_skl,snd_sof_probes,snd_soc_es8316,snd_soc_dmic
snd_rawmidi            45056  1 snd_seq_midi
snd_compress           24576  2 snd_soc_core,snd_sof_probes
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      20480  1 snd_soc_core
snd_pcm               159744  14 snd_soc_avs,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_compress,snd_soc_core,snd_sof_utils,snd_soc_skl,snd_soc_es8316,snd_hda_core,snd_pcm_dmaengine
snd_seq                77824  9 snd_seq_midi,snd_seq_midi_event,snd_seq_dummy
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              40960  3 snd_seq,snd_hrtimer,snd_pcm
snd                   114688  17 snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_sof,snd_timer,snd_compress,snd_soc_core,snd_soc_sof_es8336,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
```

---

### Post by SeijiSensei on 2023-03-08
Usually the simplest solution is to install pavucontrol. Check to make sure the default output is the speakers and not one of the HDMI ports.

[img]https://takinganimeseriously.com/images/pavucontrol.png[/img]

```
sudo apt install pavucontrol
```

---

### Post by lucant on 2023-03-09
Maybe that helps...

[https://thesofproject.github.io/latest/getting_started/intel_debug/introduction.html#:~:text=This%20will%20typically%20work%20for%20speakers%20and%20headphones/headsets%2C%20but%20will%20not%20allow%20DMIC%20capture](https://thesofproject.github.io/latest/getting_started/intel_debug/introduction.html#:~:text=This%20will%20typically%20work%20for%20speakers%20and%20headphones/headsets%2C%20but%20will%20not%20allow%20DMIC%20capture).

---

### Post by #&amp;thj^% on 2023-03-09
> **lucant said:**
> Maybe that helps...

[https://thesofproject.github.io/latest/getting_started/intel_debug/introduction.html#:~:text=This%20will%20typically%20work%20for%20speakers%20and%20headphones/headsets%2C%20but%20will%20not%20allow%20DMIC%20capture](https://thesofproject.github.io/latest/getting_started/intel_debug/introduction.html#:~:text=This%20will%20typically%20work%20for%20speakers%20and%20headphones/headsets%2C%20but%20will%20not%20allow%20DMIC%20capture).

That's a very worth while read...good post.

---

