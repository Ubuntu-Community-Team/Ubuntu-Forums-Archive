---
title: "[SOLVED] vaio external speakers from docking station problem"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by metalgtr on 2008-03-30
Hello all,

I am using a sony vaio VGN-A290 laptop running ubuntu 7.10.

My problem is that when I put my laptop onto the docking station, it does not play out of the external speakers that are standard with this laptop that came with the docking station. The problem is not with the speakers themselves because I have a dual boot with win XP and they work fine when I run on that platform.

Also on Ubuntu, the internal speakers DO work when the laptop is undocked, and I can plug other external speakers into the docking station's audio out jacks in the back when Ubuntu is running. However, I don't know how to go about configuring the external speakers, which have their own ports.

Any help on this would be appreciated.

---

### Post by lowlywrm on 2008-05-06
Similar problem for me with my VGN-A290 running Kubuntu 8.04 (Heron).  To make it work, after verifying that my sound card/driver were working properly (which I pretty much knew anyway since I could pull the laptop off the docking station and could hear the sound, then couldn't once I set it on the docking station again), I used alsamixer.  I did not mute IEC958, but I set the value for the IEC958 Playback AC97-SPSA channel to 0, and suddenly had sound again out of the speakers (which were plugged into the docking station).  All other channels are at the full 100%, unmuted, including Headphones and Aux (others had success with muting these, but I didn't).

I hope this works for you--my problem is solved.

---

### Post by whistler122 on 2008-05-12
I'm also running a VGN-A290.  Tried what you tried, but no luck.  I'm running ubuntu 8.04.  Tried the alsamixer settings you described (everything at 100 unmuted except for IEC958 at 0), but no luck.  Are the settings in realtime while fiddling with them?  I've got a cd playing and I keep pulling the computer on and off the dock to see what exactly the difference is, and it ain't really helping.

any thoughts would be appreciated.

---

### Post by metalgtr on 2008-06-14
Same here... I tried your solution but no luck. I too am running ubuntu 8.04, so perhaps Kubuntu has some drivers that Ubuntu does not. I will keep you posted if I find out anything else.

---

