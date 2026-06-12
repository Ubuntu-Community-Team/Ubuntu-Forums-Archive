---
title: "hp laptop sound lost in karmic"
date: 2009-11-07
forum: Hardware
---

### Post by saphil on 2009-11-07
HP pavilion dv6000 series.  Intel 64-bit. Standard Ubuntu internet-based upgrade from Jaunty.  Sound card HDA Intel and  ALC268.  When I look at system settings, the card is greyed out and it says "missing or no drivers."  Went to HP and they have no Linux drivers at all.  Where should I look for a new set of sound drivers?

With much helop at the Linux Install Fest today in Stlanta, I came to a few realizations:
1 I could get sound with the Ubu live disk, but once installed, the sound didn't work
2 The aplay command showed my sound card, but PPulseAudio couldn;t find the card - no output device = no sound
3 All of the sound-mods appeared to be the same on my live disk running on the machine and the installed version, but the link count was different on several, which suggests there was something less than transparent about how the installed version was running the linking.  
4 Kubuntu Live disk found the sound card.  I figured it was worth a try so I fresh-installed Kubuntu.
5 The installed version of Kubuntu found the sound card, too

So I have to assume there is a problem with the installer, and it is either not linking PulseAudio in right, or there is a problem with the compilation of PulseAudio.  KDE/Ubuntu does not appear to be using PulseAudio in the same way.  Problem  overcome but not Solved

---

