---
title: "Dell Inspiron 1420n - headphones - no sound"
date: 2009-09-10
forum: Hardware
---

### Post by Dave Kristol on 2009-09-10
I'm running Hardy on my Dell Inspiron 1420n.  Everything works great, except....  I have been unable to get output from the headphone jacks on the front.  (Sound is fine from the speakers.)  Nothing I've tried gets sound to come out, and plugging a headphone into the jack(s) does not mute the speakers.

$ aplay -l reports:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I think I've got the right settings in alsa-mixer.  Master, Headphone, PCM, Front, and Surround are all enabled, not muted, and set to reasonably high volume levels.  I've seen a variety of suggestions for settings.  One I've tried is to set "Mic as Output".

I've tried a couple of settings in /etc/modprobe.d/alsa-base, setting options snd-hda-intel model= to "dell", "dell-3stack", etc.  No luck.

Any help would be appreciated.  Thanks.
Dave Kristol

---

### Post by Zifnab06 on 2009-09-10
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Its fixed on Intrepid and Jaunty as well, if you want to do a distro upgrade. (run update-manager -d and it will find it). I had the same problem on my 1720.

---

### Post by Zifnab06 on 2009-09-10
Just a note- the instructions at the bottom that say outdated worked for me on Hardy. Just a thought though.

---

### Post by Dave Kristol on 2009-09-11
> **Zifnab06 said:**
> [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Its fixed on Intrepid and Jaunty as well, if you want to do a distro upgrade. (run update-manager -d and it will find it). I had the same problem on my 1720.

Thanks.  That's the first page I've seen (should have seen it long ago, I guess) that directs me to the set of model= options.  I'm making a little progress, I guess:  plugging the headphones into the jack(s) now mutes the speakers, but I still get no sound.  As I said before, I'm pretty sure I've got the mixer settings okay.

None of the options in ALSA-Configuration.txt match my system or sound chip, at least not exactly.  I've tried a couple of the settings, without success.  Trying them one at a time will take me more time than I can devote right now.  I'll report back if I stumble in the proper incantation.

As for upgrading to intrepid/jaunty, I'm very skittish about messing with something that's working pretty well for me.  When I try to upgrade, I want lots of time to pick up any broken pieces.  This is the ALSA version I'm running:
Advanced Linux Sound Architecture Driver Version 1.0.18.
Compiled on May  4 2009 for kernel 2.6.24-24-generic (SMP).
That looks pretty up to date.

Thanks.
Dave Kristol

---

