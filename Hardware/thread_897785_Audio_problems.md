---
title: "Audio problems"
date: 2008-08-22
forum: Hardware
---

### Post by sgtsquatlow on 2008-08-22
Hi im pretty new to linux, ive only been using it for a year or so. I have installed xubuntu on my tx2115nr laptop. I used ndiswrapper to get my wireless working but i have no audio. And i dont know the first thing involved in fixing this or changing it. ive installed alsamixergui which gives me this proc info..
/proc/asound/version:
======================
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Jun 18 2008 for kernel 2.6.24-19-generic (smp).

/proc/asound/cards:
=====================
0  [NVidia            ]:  HDA-Intel - HDA Nvidia
                          HDA Nvidia at 0xc3020000 irq 17

/proc/asound/devices:
====================
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 22: [ 0- 6]: digital audio playback
 24: [ 0- 0]: digital audio capture
 30: [ 0- 6]: digital audio capture
 33:        : timer

/proc/asound/oss-devices:
=========================
oss-devices: No such file or directory

/proc/asound/timers:
========================
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-6-0: PCM playback 0-6-0 : SLAVE
P0-6-1: PCM capture 0-6-1 : SLAVE

/proc/asound/pcm:
=======================
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-01: ALC861VD Digital : ALC861VD Digital : playback 1
00-00: ALC861VD Analog : ALC861VD Analog : playback 1 : capture 1

I have this unit dual booted so i checked vista and it said:
Realtek High Definition Audio



location: Location 0 (Internal High Definition Audio Bus)



Hardware Ids
:

HDAUDIO\FUNC_01&VEN_10EC&DEV_0862&SUBSYS_103C30E5&REV_1000

HDAUDIO\FUNC_01&VEN_10EC&DEV_0862&SUBSYS_103C30E5



address 

00000001



irq  16

Please help. Anything would be helpful at this stage. Thanks,
SgtSquatlow

---

### Post by eggdeng on 2008-08-22
Try
```
gksudo /etc/modprobe.d/alsa-base
```
Copy and paste the line
```
options snd-hda-intel model=hp
```
at the bottom of the file. Save and _reboot_. If you get no joy with this, you might try
```
options snd-hda-intel model=hp-laptop
```
More info at [http://http://ubuntuforums.org/showthread.php?t=314383](http://http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by gali98 on 2008-08-22
The snd-hda-intel driver does not have a model that works perfect for our laptop (the tx2000 series).

Really the only way to get it perfect is to modify the source code. One way to maybe get our laptop's sound better is to ask at the alsa mailing lists or the ubuntu sound mailing lists.

Kory

---

### Post by sgtsquatlow on 2008-08-24
Oh man eggdeng you are the official hero of the day. Ive been working on that for months. Thanks a ton dude. the first part did it right off the bat. Where do you go to learn stuff like that? ive read a linux+ book completely through and they sure didnt teach me that.

Thanks again,

SgtSquatlow

---

