---
title: "82801h no sound through speakers"
date: 2010-09-11
forum: Hardware
---

### Post by Grogknot on 2010-09-11
I'm not getting any sound through the speakers on an Inspiron 1520. Nothing is muted, I've checked the levels in alsamixer. The card is recognized, I can even get sound from the headjack. Only the speakers don't work. They're not broken, they worked when this laptop had windows just a few days ago.

Hope this helps

lspci | grep Audio 
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

lsmod | grep snd
```
snd_hda_codec_idt      53916  1 
snd_hda_intel          20799  2 
snd_hda_codec          87096  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5668  1 snd_hda_codec
snd_pcm_oss            34603  0 
snd_mixer_oss          13929  1 snd_pcm_oss
snd_pcm                71678  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1498  0 
snd_seq_oss            27626  0 
snd_seq_midi            4621  0 
snd_rawmidi            19141  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                48042  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18710  2 snd_pcm,snd_seq
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56687  18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7140  2 snd_hda_intel,snd_pcm
```

dpkg -l | grep alsa
```
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
rc  alsa-modules-2.6.32-24-generic                 1.0.22.1+dfsg-0ubuntu3+2.6.32-24.42             ALSA modules for kernel 2.6.32-24-generic
ii  alsa-oss                                       1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                                    1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-24-generic 2.6.32-24.17                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.24.25                                    Backported drivers for alsa-driver snapshot.

```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

head -n 1 /proc/asound/card*/codec#*
```
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9205

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

```

---

### Post by Grogknot on 2010-09-11
Still haven't figured this out yet. I've found lots of other threads with similar problems, but none of those solutions help me

---

### Post by Grogknot on 2010-09-12
bump

please help

---

