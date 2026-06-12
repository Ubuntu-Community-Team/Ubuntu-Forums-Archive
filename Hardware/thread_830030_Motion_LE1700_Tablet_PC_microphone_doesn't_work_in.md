---
title: "Motion LE1700 Tablet PC microphone doesn't work in Hardy Heron"
date: 2008-06-15
forum: Hardware
---

### Post by sarah.fauzia on 2008-06-15
From when I first installed Ubuntu (the day before yesterday) the sound has been working, but the microphone hasn't. The only fixes I tried resulted in me actually losing my sound, too, and then miraculously getting that back. From the microphone, first it was giving me no sound upon playback (using the Sound Recorder), then a terrible scratchy sound, and now an almost pleasant sound, like the sound of moving cars. But it doesn't record my voice at all.

Alsamixer tells me I have an HDA Intel Card, and a SigmaTel STAC9221 A1. 

This is what I get from alsa base:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

---

### Post by sarah.fauzia on 2008-06-15
Can anyone help? I'd truly appreciate it! :)

---

### Post by sarah.fauzia on 2008-06-16
Well, this is the only problem I still have with my Ubuntu tablet that has yet to be fixed...so again, I'm very open to helpful suggestions! :) And thanks in advance!

---

### Post by sarah.fauzia on 2008-06-16
Here is my output from amixer:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 64 [50%] [-47.25dB] [on]
  Front Right: Playback 64 [50%] [-47.25dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'Mic as Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 13 [93%] [19.50dB] [off]
  Front Right: Capture 14 [100%] [21.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%] [21.00dB] [off]
  Front Right: Capture 14 [100%] [21.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 118 [98%] [29.00dB]
  Front Right: Capture 118 [98%] [29.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 2
  Front Left: Capture 2 [100%] [20.00dB]
  Front Right: Capture 2 [100%] [20.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%] [40.00dB]
  Front Right: Capture 4 [100%] [40.00dB]

```

Again, I hope someone can helpful, and I truly thank you (beforehand!) for trying :).

---

### Post by sarah.fauzia on 2008-06-16
The solution posted [here]("http://ubuntuforums.org/showthread.php?t=827597&highlight=microphone") fixed my problem!

---

### Post by sarah.fauzia on 2008-06-20
No, it worked that day, but, somehow, when I tested it again, it doesn't work. I tried upgrading to ALSA 1.0.17 but it hasn't helped. When I try to record all I hear is crackling. Can someone help--I'd be truly grateful!

---

### Post by sarah.fauzia on 2008-06-20
FYI I have no problem with my sound--the mic is my only difficulty.

---

### Post by DrGNU on 2009-02-01
I recently acquired a used LE1600 and liberated it with Ubuntu 8.10 so far I have the pen working almost as I would like (the button only works after the tip is depressed but that is tolerable I guess).  My buttons on the machine aren't working yet... still looking for that solution (and among am concerned because I have read contradictory posts about the best method for screen rotation so right now I'm in landscape only).  Not sure how I'm going to use the pen to login either.  But for day 2 of ownership I am fairly well pleased with my progress so far.

My sound appears broken therefore I can't test the microphones.
Did this issue get resolved?

Any helpful links would be appreciated.

---

### Post by sarah.fauzia on 2009-05-24
Oh, goodness, I'm so sorry I didn't check here sooner! Well, for starters, sound worked perfectly with the LE1700. I did manage to fix the microphone when I switched to using OSS instead of ALSA, but I had some permission problems and had to do a clean install. Then again, at the time I really was a Linux newbie so I don't know if I took a stab at it again if I would get it right (I would hazard to say I would). Screen rotation isn't a problem; I used a script for ThinkPads on my LE1700 and it worked fine. What I liked about the script was that it would also rotate the navigational keys when the screen was rotated, but I couldn't manage to get that to work properly the last time I tried to change the keycodes in the script to work for the Motion.

What else... You can map the buttons using a program like xbindkeys, which is really nice because it isn't DE-dependent (DE stands for desktop environment). What you said about how your pen is working sounds very strange--I never had that problem in Intrepid. Are you using an xorg.conf? I hope you've resolved at least some of the issues you posted...

---

