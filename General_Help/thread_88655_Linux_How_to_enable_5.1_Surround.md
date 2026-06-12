---
title: "Linux: How to enable 5.1 Surround?"
date: 2005-11-10
forum: General Help
---

### Post by arcenite on 2005-11-10
Unbuntu successfully detected my soundcard but when I play music it only uses two of my speakers.  Under windows the 5.1 works fine so I know it's not the configuration of the speakers.  Any help?

Thanks!
Bill

---

### Post by cowlip on 2005-11-10
Hi, I would use alsamixer in the terminal (or alsamixer -c1 if you have another card) and turn on 3d control, turn both of those up (press m to unmute), and turn on things that say "surround"

---

### Post by garciadc on 2005-11-10
Hi
I have an Audigy 2 Platinum sound card (It was recognised without modification), and I use ALSA Mixer (Volume Control) which you can find in the Apps menu under sound and video.  There are several options and preferences you can add.  I have only 4.1, and I added Surround, PCM, EMU10K1 PCM, and EMU10K1 Send.  Don't know what your card is, but this works for me.  OH, but for some reason volume at startup is full  blast (scared the crap out of me the first time it happened), and I haven't figured out how to change this.  You may also need to change the device from onboard sound processor to your sound card (found under File>Change device.  You may need to go under System>Preferences>Multimedia Systems Selector and change output to ALSA.

---

### Post by arcenite on 2005-11-10
[QUOTE=cowlip]Hi, I would use alsamixer in the terminal (or alsamixer -c1 if you have another card) and turn on 3d control, turn both of those up (press m to unmute), and turn on things that say "surround"[/QUOTE]

Thank you sir for your input.  I did as you said and I am still only getting sound from the two speakers :(

Thanks again!
Bill

---

### Post by arcenite on 2005-11-10
Apparently I have gotten all the speakers to work except the middle speaker.  i have played with all of the options under the alsamixergui and I can't figure it out!  Any ideas?  Sub, Front, Rear, everything works... Except the center!

Thanks,
Bill

---

### Post by cowlip on 2005-11-10
[QUOTE=arcenite]Apparently I have gotten all the speakers to work except the middle speaker.  i have played with all of the options under the alsamixergui and I can't figure it out!  Any ideas?  Sub, Front, Rear, everything works... Except the center!

Thanks,
Bill[/QUOTE]

i can't get the center to work either but it MIGHT work with only dvds

---

### Post by arcenite on 2005-11-10
[QUOTE=cowlip]i can't get the center to work either but it MIGHT work with only dvds[/QUOTE]

Can we get a confirmation of some sort?  It's going to drive me nuts!

Thanks,
Bill

---

### Post by BoyOfDestiny on 2005-11-10
[QUOTE=arcenite]Can we get a confirmation of some sort?  It's going to drive me nuts!

Thanks,
Bill[/QUOTE]

on my audigy2 center works. Try playing a song with beep? I should mention I have esd disabled (have alsa-oss wrapper and libsdldebianall). Must say it works nicely, 

I've tried about 6 different apps at once and get sound (tvtime + dosbox + fceu +another fceu + beep media player + vlc). Yes it was overkill, but it works :)

---

### Post by arcenite on 2005-11-10
[QUOTE=BoyOfDestiny]on my audigy2 center works. Try playing a song with beep? I should mention I have esd disabled (have alsa-oss wrapper and libsdldebianall). Must say it works nicely, 

I've tried about 6 different apps at once and get sound (tvtime + dosbox + fceu +another fceu + beep media player + vlc). Yes it was overkill, but it works :)[/QUOTE]

What is beep?  And what is ESD?  I am a noob at work here so any help would be awesome!

Thanks,
Bill

---

### Post by MemoryDump on 2005-11-18
[QUOTE=garciadc]Hi
I have an Audigy 2 Platinum sound card (It was recognised without modification), and I use ALSA Mixer (Volume Control) which you can find in the Apps menu under sound and video.  There are several options and preferences you can add.  I have only 4.1, and I added Surround, PCM, EMU10K1 PCM, and EMU10K1 Send.  Don't know what your card is, but this works for me.  OH, but for some reason volume at startup is full  blast (scared the crap out of me the first time it happened), and I haven't figured out how to change this.  You may also need to change the device from onboard sound processor to your sound card (found under File>Change device.  You may need to go under System>Preferences>Multimedia Systems Selector and change output to ALSA.[/QUOTE]
this worked for me on my audigy 2 ZS however my trebele and bass still don't work or make a difference.. I can move the level mind you.. just no difference in sound..

any ideas?
thxs
MD

---

