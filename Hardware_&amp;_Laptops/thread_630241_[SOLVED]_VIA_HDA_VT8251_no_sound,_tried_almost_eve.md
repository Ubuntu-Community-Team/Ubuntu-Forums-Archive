---
title: "[SOLVED] VIA HDA VT8251 no sound, tried almost everything"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by balaknair on 2007-12-03
Hi
I've got a clean install of Kubuntu Gutsy (32 bit version), but I've got no sound.
Tried the ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)) and lordraiden's comprehensive sound troubleshooting guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449))

The problems I have(and as seen in the HdaIntelSound)Howto

High pitched noise
Poor sound quality
Sound disappears when touching volume controls
Sound works at random after each reboot


Nothing works. The funny thing is I had the exact same sound issues with Feisty, and it worked flawlessly after following the HdaIntelSoundHowto (for that matter, I used the same HowTo to fix this problem with Mandriva 2008, just substituting urpmi for apt-get). But when I tried it with Gutsy, it just stopped recognizing my sound card on reboot(no sound card found), and then nothing short of a clean install of Gutsy seems to fix that. Recompiling ALSA kernel makes no difference. Tried just about all the workarounds I found here. Only this time(I've reinstalled Gutsy 4 times in the past 5 days just because of this) I've managed to get nearly everything else working, I don't want to screw up again and mess it up, so much as I regret the inconvenience to you folks, it's time for me to log back in to ubuntuforums and scream "HELP". Please do help me.

And another thing is (I'm not sure how relevant this is) the ALSA index suggests the module I need is snd-hda-intel, but typing aplay -l in konsole the output I get is
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).


If there's anything else you need me to find out, please say so. I'll be checking this thread every 15 minutes or so. So I'll reply ASAP.

---

### Post by balaknair on 2007-12-03
OK I think I finally got it working. 5 hours and God knows how many reboots later, I've got crystal clear sound(just hope it stays after my next reboot):guitar:

basically just used ALSA 1.0.14 snd-hda-intel(earlier I'd compiled ALSA 1.0.15, which worked in Mandriva 2008 )
then in konsole
```
sudo nano /etc/modprobe.d/alsa-base

```

and edited it by pasting
```
options snd-hda-intel model=3stack
```


A big thanks to everyone
Hope someone finds this useful.:KS

PS: Maybe this seems to suggest some issue with ALSA 1.0.15 and Ubuntu Gutsy?
I have no clue if this is something to do with my stupidity or if it's a compatibility issue between ALSA 1.0.15 and Gutsy for the HDA-Intel module, so I hope someone with more sense than I have gives it a closer look if there is some issue

---

