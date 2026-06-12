---
title: "SB - OSS or Windows Reboot - any other solution??"
date: 2011-01-28
forum: Hardware
---

### Post by arunvir on 2011-01-28
HI,

Its been really quite some time since I have had to step into ubuntu community. Ubuntu did some wonders for my laptop. 

I wish the same to come true for my PC.

Simple Problem:-

Sound doesnt work on direct boot into ubuntu. Boot into window box and come back. It works like a baby. I boot directly against my sound cards wishes and my sound card gives me ghost voice.

Tough Solution:-

I know OSS is there. But let me confirm my problem. I'm not good at compiling the source and especially the part where I have to do some linking with the kernel source.

And I have confirmed from the internet that the .deb will ask you for license soon.

I'm very happy with pulse, If I can get this single problem out of the way somehow.

Simple Solution:-

Let me know on any kind conf file change that you think I can do. I know there were many ppl who wanted to fix this. So someone among you would have found a simple solution. :guitar:

Share it and you shall be blessed!!!

My new baby details-

lspci|grep audio
03:00.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

(I have turned off my inbuilt system sound card in BIOS(Gigabyte G31MES2L).)

lsmod|grep snd
snd_ca0106             31531  1 
snd_ac97_codec        100646  1 snd_ca0106
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  12 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_ca0106,snd_pcm
(it would be great if you could tell me what these numbers mean)

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.

 cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      AudigyLS [Unknown] at 0xd000 irq 20

cat /proc/asound/devices 
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: raw midi
  5: [ 0- 3]: digital audio playback
  6: [ 0- 3]: digital audio capture
  7: [ 0- 2]: digital audio playback
  8: [ 0- 2]: digital audio capture
  9: [ 0- 1]: digital audio playback
 10: [ 0- 1]: digital audio capture
 11: [ 0- 0]: digital audio playback
 12: [ 0- 0]: digital audio capture
 13: [ 0]   : control

cat /proc/asound/timers 
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-1-1: PCM capture 0-1-1 : SLAVE
P0-2-0: PCM playback 0-2-0 : SLAVE
P0-2-1: PCM capture 0-2-1 : SLAVE
P0-3-0: PCM playback 0-3-0 : SLAVE
P0-3-1: PCM capture 0-3-1 : SLAVE

cat /proc/asound/pcm 
00-00: ca0106 : CA0106 : playback 1 : capture 1
00-01: ca0106 : CA0106 : playback 1 : capture 1
00-02: ca0106 : CA0106 : playback 1 : capture 1
00-03: ca0106 : CA0106 : playback 1 : capture 1

I would love to provide more details as needed. I would also like to understand this issue more. I love to read.:-({|=

---

### Post by arunvir on 2011-01-28
I will reply to replies within a day at the most. =D>
Reason:-
All internet sites are blocked in my office due to :twisted:security :twisted:constraints.

---

