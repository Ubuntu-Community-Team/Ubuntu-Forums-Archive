---
title: "Sound stopped working from Edgy beta to Edgy RC1"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by ktraub on 2006-10-24
Hello all;
I have Edgy running on a Dell Inspiron 9400 laptop and the sound stopped working from Edgy Beta to Edgy RC1.
When I run lsmod | grep snd I get:

root@opclaptop2:~# lsmod | grep snd
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    58372  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
dprobe snd-hda-intel

Also, when I run: aplay -l I see:

mod**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
probe snd-hda-intel

If I open the Sound preferences I can hear sound from the OSS Sound System but not the Stac 9200 analog nor the Alsa devices.

Also, I hear no system sounds with Edgy RC1, but they work fine if I boot the Edgy Beta CD.

Any help is greatly appreciated.
-Kev

---

### Post by ktraub on 2006-10-24
After some searching, found the following solution for the no sound issue with the Intel HD sound chipset.
Add the following lines to the /etc/modprobe.d/options file:
# fix intel sound
options snd_hda_intel model=3stack

---

