---
title: "Intrepid Sound does not work on loudspeakers"
date: 2009-01-21
forum: Hardware
---

### Post by beroot on 2009-01-21
Hi,

I have installed Ubuntu Intrepid on a laptop Packard Bell EASYNOTE SL65-M-014FR. Everything works fine except the sound on the loudspeakers.
It works on the headphone plug.
The sound is configured at the maximum level with alsamixer.

Any idee about the problem ?

Thanks for your help

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]

**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : HDA Generic [HDA Generic]
  Sous-périphériques: 0/1
  Sous-périphérique: #0: subdevice #0
carte  1: HDMI [HDA ATI HDMI], périphérique 3 : ATI HDMI [ATI HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0


&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.17 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: PulseAudio                                                             &#9474;
&#9474; Chip: PulseAudio                                                             &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master

---

### Post by beroot on 2009-01-21
If someone could help me...

---

### Post by beroot on 2009-01-22
No idea about my problem ?

---

### Post by markbuntu on 2009-01-22
There seems to be a problem with the snd_hda_intel alsa driver. It needs to be configured properly for your hardware. There is a listing here for the packard-bell easynote that will tell you which option to try first and how to do it


[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

