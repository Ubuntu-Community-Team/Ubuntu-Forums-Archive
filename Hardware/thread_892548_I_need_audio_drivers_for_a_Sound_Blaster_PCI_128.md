---
title: "I need audio drivers for a Sound Blaster PCI 128"
date: 2008-08-17
forum: Hardware
---

### Post by The Beanjamin on 2008-08-17
Hello,

I'm fairly new to Ubuntu, and I'd like to know how I can get audio drivers for my sound card. I think it's a Sound Blaster PCI 128, but I'm not 100% sure. I'd appreciate it if someone could tell me how I can confirm this. 
Anyway, I need audio drivers for this card, because sometimes I can't hear any sound, or the sound is just about 1 second too late, which is quite annoying. I tried searching for this on the Internet, but couldn't find anything, apart from a couple of Windows drivers. 

Any help is appreciated.

---

### Post by drboontu on 2008-08-17
Hi,

Sound info

post back what is returned when you type these in a terminal:

$ lspci | grep -i audio

$ cat /proc/asound/modules

$ cat /proc/asound/devices

$ lsmod | grep snd

Cheers,

---

### Post by The Beanjamin on 2008-08-17
Ok, here is the output:

benjamin@Linux:~$ lspci | grep -i audio
02:00.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 04)
benjamin@Linux:~$ cat /proc/asound/modules
 0 snd_ens1371
 1 snd_mpu401
benjamin@Linux:~$ cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
  8: [ 0- 0]: raw midi
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 32: [ 1]   : control
 33:        : timer
 40: [ 1- 0]: raw midi
benjamin@Linux:~$ lsmod | grep snd
snd_ens1371            27168  3 
snd_ac97_codec        101028  1 snd_ens1371
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_mpu401              9448  0 
snd_mpu401_uart         9728  1 snd_mpu401
snd_seq_midi            9376  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25760  3 snd_ens1371,snd_mpu401_uart,snd_seq_midi
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    56996  19 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  1 snd_pcm
gameport               16008  2 snd_ens1371,analog

---

### Post by The Beanjamin on 2008-08-17
Anyone?

---

### Post by The Beanjamin on 2008-08-18
I really don't know what to do, please help.

---

