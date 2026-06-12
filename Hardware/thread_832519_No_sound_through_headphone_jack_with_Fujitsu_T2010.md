---
title: "No sound through headphone jack with Fujitsu T2010"
date: 2008-06-17
forum: Hardware
---

### Post by everdred on 2008-06-17
I've been through countless threads so far and have even added my information to [this bug, which has not received any attention]("https://bugs.launchpad.net/ubuntu/+bug/209057"), but still haven't found a way to get sound working though my laptop's headphone jack. 

My laptop is a Fujitsu T2010. In Hardy, sound plays through the internal speaker, but not through the headphone jack. This worked in Gutsy (though only by manually enabling the "Headphone" switch under Gnome Volume Control), but this workaround no longer works.

I've tried both with and without PulseAudio running, and there's no luck either way.

I saw some advice for using alsamixer to change the "Headphone" volume (a slider for this channel does not appear in Gnome's Volume Control), but in alsamixer, "Headphone" is permanently stuck at 00.

If this helps...

```
lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

```
lsmod | grep snd
snd_hda_intel 344600 3
snd_pcm_oss 42144 0
snd_mixer_oss 17920 1 snd_pcm_oss
snd_pcm 78596 2 snd_hda_intel,snd_pcm_oss
snd_page_alloc 11400 2 snd_hda_intel,snd_pcm
snd_hwdep 10500 1 snd_hda_intel
snd_seq_dummy 4868 0
snd_seq_oss 35584 0
snd_seq_midi 9376 0
snd_rawmidi 25760 1 snd_seq_midi
snd_seq_midi_event 8320 2 snd_seq_oss,snd_seq_midi
snd_seq 54224 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 24836 2 snd_pcm,snd_seq
snd_seq_device 9612 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 56996 17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 8800 1 snd
```

Absolutely any assistance anyone can provide is appreciated.

---

### Post by everdred on 2008-10-08
This is, by the way, working in Intrepid.

---

### Post by Amorget on 2008-10-13
I have this exact same problem with my Sony VGN-AR670, my soundcard is identical to yours.

Really annoying...

Douglas

---

