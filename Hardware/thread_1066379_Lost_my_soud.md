---
title: "Lost my soud"
date: 2009-02-10
forum: Hardware
---

### Post by firasalkhalil on 2009-02-10
hi,
I have Ubuntu 8.10 on Dell Inspiron 6400, wih INTEL built-in sound card...:KS
First of all, i wanted to make Audacity work, so after a couple of researches i tried to download the newest alsa packages, compile and install them...:popcorn:
Audacity worked very well, but after a restart, i lost the sound, so i did other researches, and i was told to kill pulse audio (via killall pulseaudio) : it worked... after a second restart... no sound too, so i tried the previous trick but it didnt work!!
I tried to reinstall the drivers from sources like the official ubuntu sound troubelshouting page instructed, but i got boguusss!!!
now when i try to test sounds from system->preferences->sounds i get : "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosinc : Could not open audio device for playback."
and when i try to change the volume from the panel i get : "No volume control GStreamer plugins and/or devices found"](*,)](*,)](*,)

please i am very desperate... its been 4 days without even a PC BEEP !:confused: :(

---

### Post by martinbaselier on 2009-02-10
What's the output of:
```

lspci | grep Audio
lsmod | grep snd

```

---

### Post by firasalkhalil on 2009-02-11
> lspci | grep Audio 
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

> lsmod | grep snd
```
snd_pcm_oss            46496  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                83716  1 snd_pcm_oss
snd_seq_oss            39936  0 
snd_seq_midi_event     15232  1 snd_seq_oss
snd_seq                58352  4 snd_seq_oss,snd_seq_midi_event
snd_timer              29448  2 snd_pcm,snd_seq
snd_seq_device         15500  2 snd_seq_oss,snd_seq
snd                    62372  7 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16776  1 snd_pcm

```

---

