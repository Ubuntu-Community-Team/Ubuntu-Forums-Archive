---
title: "Fast Fowarding Videos/Music Ubuntu 9.10 RC"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by yuxinzhu93 on 2009-10-25
I just download Ubuntu 9.10 RC, videos and music worked fine in 9.04, but in 9.10, my music and videos (on my computer, and on websites like youtube) just play super fast, and skips around usually without sound 

any ideas?

[edit] reinstalled also driver, speed problem fixed, but still no sound

---

### Post by Fosters on 2009-10-31
I have the same problem

did you had OSS or ALSA before ?

mine was OSS 

I always had some small problems (2 sound cards) but this time I can't find a solution :o(

00:0e.0 Multimedia audio controller: Fortemedia, Inc Xwave QS3000A [FM801] (rev b2)
00:0e.1 Input device controller: Fortemedia, Inc Xwave QS3000A [FM801 game port] (rev b2)
...
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)


$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_hda_intel          26920  0 
snd_hda_codec          75708  1 snd_hda_intel
snd_fm801              16800  1 
snd_tea575x_tuner       5052  1 snd_fm801
videodev               36736  1 snd_tea575x_tuner
v4l1_compat            14496  1 videodev
snd_opl3_lib           10396  1 snd_fm801
snd_via82xx            23576  0 
snd_hwdep               7200  2 snd_hda_codec,snd_opl3_lib
snd_mpu401_uart         6940  2 snd_fm801,snd_via82xx
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_ac97_codec        101216  2 snd_fm801,snd_via82xx
iptable_filter          3100  0 
snd_seq_midi            6432  0 
ac97_bus                1532  1 snd_ac97_codec
snd_rawmidi            22208  2 snd_mpu401_uart,snd_seq_midi
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
x_tables               16544  1 ip_tables
snd_mixer_oss          16028  1 snd_pcm_oss
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                75296  6 snd_hda_intel,snd_hda_codec,snd_fm801,snd_via82xx,snd_ac97_codec,snd_pcm_oss
psmouse                56180  0 
snd_timer              22276  3 snd_opl3_lib,snd_seq,snd_pcm
serio_raw               5280  0 
fm801_gp                2780  0 
k8temp                  4188  0 
shpchp                 32272  0 
ppdev                   6688  0 
i2c_viapro              7312  0 
snd_page_alloc          9156  3 snd_hda_intel,snd_via82xx,snd_pcm
snd                    59204  18 snd_hda_intel,snd_hda_codec,snd_fm801,snd_opl3_lib,snd_via82xx,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
gameport               11368  3 snd_via82xx,fm801_gp
soundcore               7264  1 snd
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp


Can anybody HELP PLEASE ?

---

### Post by Fosters on 2009-11-08
gave up 9.10 back tu 9.04 where everything works fine !

---

