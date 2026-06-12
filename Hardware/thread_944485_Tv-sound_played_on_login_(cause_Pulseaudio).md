---
title: "Tv-sound played on login (cause: Pulseaudio)"
date: 2008-10-11
forum: Hardware
---

### Post by The_3cHeLoN on 2008-10-11
I hear TV-sound at login, the sound of an off-channel frequency. I have a pctv stereo TV-card, the audio-port is connected in the cd-in on the mobo (that was never a problem on Ubuntu < 8.04). Look at this video for better explanation [http://www.youtube.com/watch?v=t_fz861sr3o]("http://www.youtube.com/watch?v=t_fz861sr3o")

The sound occurs only when Pulseaudio starts, so if I do a /etc/init.d/pulseaudio force-reload  I hear the sound and get the following output:

```
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.front.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM front:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround40.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround40:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround51.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround41:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround51.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround50:1
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround51.0:CARD=1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround51:1
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 1
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround71:1
W: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Cannot find fallback mixer control "Mic".

```

How can I fix this problem?

---

