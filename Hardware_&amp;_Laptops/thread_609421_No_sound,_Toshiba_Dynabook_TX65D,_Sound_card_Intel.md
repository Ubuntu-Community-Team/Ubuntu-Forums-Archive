---
title: "No sound, Toshiba Dynabook TX/65D, Sound card: Intel 82801G (ICH7 Family) (2nd post~"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by uuser_ms on 2007-11-10
Hi
I have big problems to get sound on my new Toshiba Dynabook TX/65D Laptop. I installed Ubuntu 7.10 already few times with different settings. Kubuntu 7.10 too. Nothing helps. There is no sound when trying to play anything. Alsa is 1.0.15. Volumes in alsamixer and all other mixer applications are 100% and there is definitely no mute setting turned on. Still no sound.

lspci output :
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

cat /proc/asound/cards output;
0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xf0b40000 irq 21

lsmod | grep snd:
snd_rtctimer 4384 0
snd_hda_intel 263712 1
snd_pcm_oss 44672 0
snd_mixer_oss 17664 1 snd_pcm_oss
snd_pcm 80388 2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 33152 0
snd_seq_midi 9600 0
snd_rawmidi 25728 1 snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
snd_seq 53232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 24324 3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
snd 54660 11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_de vice
soundcore 8800 1 snd
snd_page_alloc 11400 2 snd_hda_intel,snd_pcm

Ive been struggling with it for few weeks already and I cant get any sound. I would be gratefull for any help.
Ubuntu User

---

### Post by bharris25 on 2007-11-11
Try adding to /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

Then reboot and see if that works.:guitar:

---

### Post by uuser_ms on 2007-11-13
Thanks for help but unfortunately it doesnt work. Nor does the options auto and toshiba.
Still no sound. Please help.
Ubuntu User

---

