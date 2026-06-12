---
title: "HDA Intel ALC 268 sound card stopped working"
date: 2009-02-11
forum: Hardware
---

### Post by raunhar on 2009-02-11
After installing Ubuntu 8.10, the sound was fine.
But one day it suddenly went off. I did a lot of reserach though the forum but no success.
When I go to Pref. -->Sound--> and select HDA Intel ALC268 Analog (ALSA) and give test, I get he result 
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

For all other options, I never get any result. Autodetect just keeps testing pipeline and does nothing.

I am attaching the etxt file with all the R&D that I did.

I am very much new to LINUX and hence do hope for a solution (an early solution would be appreciated).

lspci | grep audio  
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

lsmod | grep snd
nd_pcm_oss            46848  0 
snd_mixer_oss          22784  2 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  2 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm

---

### Post by raunhar on 2009-02-11
For the time being Solved:
Did this:
options snd-hda-intel enable_msi=1


Added to the last
options snd-hda-intel enable_msi=1

---

### Post by LoGraYThS on 2009-03-06
Hey,

I'm having the same problem with this after upgrading ALSA drivers for my Acer Aspire One with Eeebuntu Standard.

Here's the thread I just created explaining the problem, cause it's a little different than yours.

[http://ubuntuforums.org/showthread.php?t=1088868](http://ubuntuforums.org/showthread.php?t=1088868)

I can hear sound but only after a few seconds I launch one.

How you fixed your problem exactly?

Where you inserted those strings?

Thank you in advance.

---

