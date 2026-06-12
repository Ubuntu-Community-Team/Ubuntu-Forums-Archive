---
title: "Suddenly no sound output"
date: 2013-11-06
forum: Hardware
---

### Post by arnold_layne2 on 2013-11-06
[13.04] My sound was working perfectly, but today when i booted up my computer, I'm getting no sound output. Here's what I've already tried:

1. Restarting computer
2. Restarting pulseaudio
3. Checking alsamixer
4. Reinstalling pulseaudio and alsa

>  $ aplay -l | grep card
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
> 
$ sudo lsmod | grep snd
snd_hda_intel          39619  8 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  25 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd




I'm kind of lost, none of the common solutions seem to be working. Sound works in windows.

EDIT: In Sound Settings, 'Analog Output' is the only device visible.

---

