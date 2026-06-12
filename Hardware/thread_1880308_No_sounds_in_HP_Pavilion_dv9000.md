---
title: "No sounds in HP Pavilion dv9000"
date: 2011-11-13
forum: Hardware
---

### Post by collinsauve on 2011-11-13
I recently installed Lucid on my dv9000.   I have been able to get everything else(that I've tried) working except the sound.   I've been at this for about 2 hours now so thought it was time to ask for help :)


```

**user@computer:~$ lspci | grep Audio**
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

```

**user@computer:~$ lsmod | grep snd**
snd_hda_codec_conexant    36605  1 
snd_hda_intel          23768  1 
snd_hda_codec          99419  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6938  1 snd_hda_codec
snd_pcm_oss            40601  0 
snd_mixer_oss          16474  1 snd_pcm_oss
snd_pcm                88141  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            31490  0 
snd_seq_midi_event      7267  1 snd_seq_oss
snd_seq                57524  4 snd_seq_oss,snd_seq_midi_event
snd_timer              23021  2 snd_pcm,snd_seq
snd_seq_device          7112  2 snd_seq_oss,snd_seq
snd                    72167  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8628  2 snd_hda_intel,snd_pcm

```


```
**user@computer:~$ cat /proc/asound/card0/codec#* | grep Codec**
Codec: Conexant CX20549 (Venice)

```

[LIST]
[*]alsaconf does not detect it.
[*]From the approx 50 pages I've read, I am fairly convinced I need to use snd-hda-intel
[/LIST]
What I've tried:

[LIST]
[*]Recompiled alsa to 1.0.23 with --with-cards=hda-intel --with-sequencer=yes [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)
[*][https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) my codec does not exist in HD-Audio-Models.txt.gz
[*]also tried various pages telling me to edit alsa-base.conf and /etc/modules
[*]used alsamixer to ensure channel volumes are turned up
[/LIST]

---

