---
title: "Baffling problem with sound"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by edwardian on 2006-06-13
I installed Ubuntu 6.06 last week, and I am having a baffling problem with my sound.  Sometimes it works, sometimes, for no apparent reason, it doesn't.  After lengthy tinkering, I have found that if I boot from CD (any CD, not necessarily the Ubuntu CD), the next time I boot up, the sound will be working.  Otherwise, no sound.

Sound card is a VIA 8237, optical drive is a Samsung TS-H552U

ed@Ubuntu:~$ lsmod |grep -1 snd
lp                     11844  0
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
tsdev                   8000  0
nvidia               4550772  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
shpchp                 45632  0
--
parport                36296  3 ppdev,lp,parport_pc
snd_via82xx            28824  1
gameport               15496  1 snd_via82xx
snd_ac97_codec         92704  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55268  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
floppy                 62148  0
soundcore              10208  1 snd
pcspkr                  2180  0

Any thoughts on this would be much appreciated.

---

### Post by mozkill on 2006-06-14
i have had sound problems when installing the distro using the "custom" option where you can choose the packages that you want.

if you use one of the pre-configured options instead, your sound will very likely work.

also, i recommend using the "Automatix" script to setup your sound...

good luck and hopefully i hit the hammer with the nail...

---

### Post by edwardian on 2006-06-16
A good thought, but no.  Still having the same problem.

---

### Post by mozkill on 2008-02-29
sorry that didnt work.  maybe your motherboard needs a bios upgrade that supports later Ubuntu distros?  your description does sorta imply that you have a bios bug.

---

