---
title: "sound not working (after update)"
date: 2009-02-20
forum: Hardware
---

### Post by miroslav_karpis on 2009-02-20
Hi all,
am just getting in more and more hopeless mood after the last problems :( ..the new is that the sound stopped to work. Just installed couple of updates and....quite.

Here is my lsmod | grep snd:

snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm



please can anybody help?

---

### Post by Sportingfan on 2009-02-20
Same problem here.
After an update I lost my sound. After reading several threads, I succeeded to get my sound back, but the volume is very low.

Some outputs:

lsmod | grep snd
```
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Two months ago, I installed Intrepid and my sound didden't work. After reading some threads I found that I had to add 
```
options snd-hda-intel model=mobile
```
to the file /etc/modprobe.d/alsa-base. This made my 
sound work perfectly. But now it's broken, AGAIN.

---

### Post by geirha on 2009-02-20
My sound disappeared after an update as well, but I don't remember which update. It turned out one of the channels, "AUX" in my case, had been muted. Unmuting it got the sound back. Check all volume controls.

---

### Post by miroslav_karpis on 2009-02-20
> **geirha said:**
> My sound disappeared after an update as well, but I don't remember which update. It turned out one of the channels, "AUX" in my case, had been muted. Unmuting it got the sound back. Check all volume controls.

pls. can you give me some hints that how can I do that?

---

### Post by geirha on 2009-02-20
Double click the speaker icon on the top panel to get to the gnome-volume-control. Click on the Preferences button, mark all channels of type playback and close. Try unmuting and raising the volume lever on some or all of the playback channels and see if you get any sound (play some music in rythmbox or similar while you try this).

---

### Post by miroslav_karpis on 2009-02-20
worked - VERY much thankful

---

### Post by Sportingfan on 2009-02-20
Worked for me too!

THX!

---

