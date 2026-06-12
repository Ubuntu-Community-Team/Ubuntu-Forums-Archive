---
title: "No audio"
date: 2008-11-22
forum: General Help
---

### Post by feedmecereal on 2008-11-22
I have no sound at all. When I go into Preferences --> Sound and I try to test sound events or any other of the options, I get the following error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I have been having this issue ever since I upgraded from 8.04 to 8.10. Sometimes the sound plays at a low volume when I first start Ubuntu but then disappears completely.

---

### Post by hal8000 on 2008-11-22
We need to collect some information, first your sound card. From the terminal post the soutput of:

lspci | grep audio
lspci | grep snd

Then your kernel version and which (if any) modules are loaded:

uname -a
lsmod | grep snd

---

### Post by feedmecereal on 2008-11-22
The first two did nothing but with the second two I got some output:

```
danny@danny-desktop:~$ lspci | grep audio
danny@danny-desktop:~$ lspci | grep snd
danny@danny-desktop:~$ uname -a
Linux danny-desktop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux
danny@danny-desktop:~$ lsmod | grep snd
snd_hda_intel         381488  4 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
danny@danny-desktop:~$ 

```

---

