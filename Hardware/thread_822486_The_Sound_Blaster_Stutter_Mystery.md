---
title: "The Sound Blaster Stutter Mystery"
date: 2008-06-08
forum: Hardware
---

### Post by DiplomFrucht on 2008-06-08
I am using a Sound Blaster Live! 5.1 (SB0100) on a MSI P965 Neo board. In Windows and before i log in to Ubuntu, the sound is working (the drum roll can be heard just fine). But once i log in, all I get is a terrible stutter-like sound, as if it is repeating the first few milliseconds of the file in an infinite loop. All sound is afflicted: MP3s, wavs, speaker-test and even /dev/dsp (the latter to a lesser extent, longer bits of sound with less interruptions/repeats).
Pulseaudio doesn't affect the stuttering at all, I actually got it in an attempt to fix the problem.
I've talked to a few people on IRC about it and everything seems to be set up properly.
When I click Test in the Sound Preferences window, I get a loud beeping noise and sometimes the whole thing crashes and needs to be force closed. 
I also get the identical problem using the Live CD.

PS Aux: [http://pastebin.com/m1ae647d7](http://pastebin.com/m1ae647d7)
lsmod: [http://pastebin.com/mcea2e8](http://pastebin.com/mcea2e8)

Anything anyone? :)

Edit: Mystery solved. My undetected SATA drives connected via a JMicron controller were causing the stuttering.
Edit2: For those finding this via Google: adding "acpi=off all-generic-ide irqpoll" to the kernel line in Grub fixed the whole problem.

---

