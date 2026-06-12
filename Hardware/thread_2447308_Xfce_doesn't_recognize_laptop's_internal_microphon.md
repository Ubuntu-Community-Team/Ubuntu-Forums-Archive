---
title: "Xfce doesn't recognize laptop's internal microphone"
date: 2020-07-16
forum: Hardware
---

### Post by lucasgossen on 2020-07-16
Hello, I have a Dell Inspiron N4050 running xubuntu. The system doesn't recognize my internal microphone (only Monitor appears on audio mixer) unless I plug and then unplug an external microphone. Then, the laptop's internal microphone appears on mixer and I can select it, and it works fine. But if I don't plug an external one, there's no way to make the laptop's microphone visible to the system, wheter I want to use it on audacity or firefox, nothing can find it.

I don't have the same problem in other distros (including standard ubuntu), so I believe it's not a hardware issue.

I'm gonna post here some outputs that I think could help you guys understand what's going on here, because I couldn't figure it out...

# inxi -Fxz
```

 Audio: Card-1 Intel Broadwell-U Audio Controller driver: snd_hda_intel
           Card-2 Intel Wildcat Point-LP High Def. Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k5.3.0-62-generic 
```

# lsmod | grep snd_hda_intel
```
 snd_hda_intel          53248  4
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd                    86016  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi 
```

# dmesg | grep audio
```
 [   11.176939] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   12.054570] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC3234: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   12.054573] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.054574] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   12.054575] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[   12.054576] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[   12.054578] snd_hda_codec_realtek hdaudioC1D0:      Headset Mic=0x19
[   12.054579] snd_hda_codec_realtek hdaudioC1D0:      Headphone Mic=0x1a
[   12.054581] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12 
```

# aplay -l
```
 placa 1: PCH [HDA Intel PCH], dispositivo 0: ALC3234 Analog [ALC3234 Analog]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0 
```

Thank you all for your help!

PS: Sorry for the portuguese: "placa" means something like "board", "card" or "chipset"; and "Dispositivo secundário" means "secundary device"

---

