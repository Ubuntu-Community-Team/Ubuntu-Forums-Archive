---
title: "AMD proprietary graphics driver influences sound output"
date: 2012-04-19
forum: Hardware
---

### Post by brainwash on 2012-04-19
Hey,

I have a weird problem with the proprietary graphics driver for my ATI/AMD card (installed via jockey). When I move a window / use a scrollbar while listening to music or when I watch a flash video in fullscreen mode, my speakers start to make this crackling noise.

Can't reproduce this issue with the the open source driver (radeon) and it is not a problem related to Pulseaudio.

Maybe anyone knows how to solve this conflict, because I need 3D acceleration AND clean sound.

Many thanks
brainwash

```
brainwash@local:~$ **uname -a**
Linux local 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 i686 i386 GNU/Linux
```
```
brainwash@local:~$ **fglrxinfo**
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5670
OpenGL version string: 4.2.11627 Compatibility Profile Context
```
```
brainwash@local:~$ **apt-cache policy fglrx**
fglrx:
  Installed: 2:8.960-0ubuntu1
  Candidate: 2:8.960-0ubuntu1
```
```
brainwash@local:~$ **lspci | grep -i audio**
04:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]
05:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
```
```
brainwash@local:~$ **lsmod | grep snd**
snd_emu10k1_synth      12963  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13526  1 snd_emux_synth
snd_hda_codec_hdmi     31775  1 
snd_emu10k1           133257  6 snd_emu10k1_synth
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_hdmi,snd_hda_intel
snd_ac97_codec        106082  1 snd_emu10k1
snd_seq_midi           13132  0 
ac97_bus               12642  1 snd_ac97_codec
snd_rawmidi            25424  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_pcm                80845  6 snd_hda_codec_hdmi,snd_emu10k1,snd_hda_intel,snd_hda_codec,snd_ac97_codec
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13276  3 snd_emux_synth,snd_emu10k1,snd_hda_codec
snd_seq                51567  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              28931  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14172  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  28 snd_emux_synth,snd_seq_virmidi,snd_hda_codec_hdmi,snd_emu10k1,snd_hda_intel,snd_hda_codec,snd_ac97_codec,snd_rawmidi,snd_pcm,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  3 snd_emu10k1,snd_hda_intel,snd_pcm
```
```
brainwash@local:~$ **aplay -l | grep card**
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
card 1: Live [SB Live! 5.1 [SB0220]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
card 1: Live [SB Live! 5.1 [SB0220]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
card 1: Live [SB Live! 5.1 [SB0220]], device 3: emu10k1 [Multichannel Playback
```

---

### Post by brainwash on 2012-04-20
bump :-k

---

### Post by brainwash on 2012-04-23
Well, the sound chip is pretty old and I was not able to find a solution to remove or reduce the crackling noise by changing the ALSA/Pulseaudio configuration. Adjusting CPU priorities or IRQ latencies did not help either.

So I disabled display compositing and additionally the XRender extension (Xorg). Firefox uses the Cairo library, which uses the XRender backend for hardware acceleration. As we all know, Adobe's Flash Player does not support hw acceleration on linux systems, the corresponding option to disable it can be ignored.

Now I got clean sound and no major downsides! :)

---

