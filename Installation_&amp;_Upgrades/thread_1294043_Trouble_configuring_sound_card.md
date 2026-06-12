---
title: "Trouble configuring sound card"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by swappo1 on 2009-10-17
Hello, I am having trouble configuring my sound card.  If I run #alsaconf it will set up my sound card to where I can play a cd and some video(with sound) on the internet.  However I can't play sound from mplayer or Movie player.  Mplayer says: could not open/initialize audio device.  Also, I have to run alsaconf everytime I reboot to reconfigure the sound because the changes are not being saved.
lsmod | grep snd:
```
hopchewer@hopchewer:~$ lsmod | grep snd
snd_hda_intel         436696  1 
snd_pcm_oss            41760  0 
snd_mixer_oss          18816  1 snd_pcm_oss
snd_pcm                81800  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           7428  0 
snd_seq_oss            33152  0 
snd_seq_midi           11072  0 
snd_rawmidi            26784  1 snd_seq_midi
snd_seq_midi_event     11904  2 snd_seq_oss,snd_seq_midi
snd_seq                54304  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25744  2 snd_pcm,snd_seq
snd_seq_device         11668  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63688  10 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12064  1 snd
snd_page_alloc         13072  2 snd_hda_intel,snd_pcm

```
lspci | grep Audio
```
hopchewer@hopchewer:~$ lspci | grep Audio
00:07.0 Audio device: nVidia Corporation Device 0774 (rev a1)

```
aplay -l
```
hopchewer@hopchewer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I am using Debian Lenny on an amd64.  How do I configure my sound card correctly so that I can play all sound and so it stays configured when I shut my computer off?

---

### Post by swappo1 on 2009-10-18
Nobody knows how to troubleshoot a soundcard?

---

### Post by swappo1 on 2009-10-19
38 views and not one single person can offer any help?

---

