---
title: "ES1978 Maestro 2E sound problems (echo, bad sync etc..)"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by tuxzilla on 2006-10-29
Since installing Xubuntu I've been having sound problems. Playing DVDs I get lots of distortion, playing .mpg or mp3 files, the first first second sounds fine then left and right speakers quickly lose sync giving a wierd echo effect and static builds up on the left speaker. Strangely quicktime and mpeg4 with mp3 audio seem to better. I've tried multiple players (xmms, mplayer, xine, mpg123), I've tried purging and reinstalling alsa. I've tried compiling Mplayer from source. Sound was working fine on Yoper and Mandrake before that. Any suggestions are welcome.


lspci returns:
...
0000:00:10.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
...


lsmod shows the right module is installed:
snd_es1968             30848  2
gameport               15496  1 snd_es1968
snd_ac97_codec         93216  1 snd_es1968
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
snd_pcm                89864  3 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_page_alloc         10632  2 snd_es1968,snd_pcm
snd_mpu401_uart         7808  1 snd_es1968
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  1 snd_rawmidi
snd                    55268  11 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device


and finally aplay -l returns:
**** List of PLAYBACK Hardware Devices ****
card 0: E2E [ESS ES1978 (Maestro 2E)], device 0: ESS Maestro [ESS Maestro]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3

---

### Post by gedden on 2007-11-26
I have this same problem with a compaq armada m300, any ideas out there?

---

