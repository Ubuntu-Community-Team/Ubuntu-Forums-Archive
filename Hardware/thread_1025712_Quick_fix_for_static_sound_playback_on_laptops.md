---
title: "Quick fix for static sound playback on laptops"
date: 2008-12-30
forum: Hardware
---

### Post by mpadams on 2008-12-30
My Toshiba laptop has a real annoying problem with static on sound playback. I did notice some attempt by the OS to blacklist snd_pcsp with a patch, but not everyone has used this. Someone else proposed modifying the sink for PulseAudio, but that's an overkill solution IMO.

1. Open a terminal
2. sudo nano /etc/modprobe.d/blacklist
3. Add the following...

[I]# Sound-fix      
blacklist pcspkr
blacklist snd_pcsp
[/I]
4. Save & reboot

[Reference link]("http://ubuntuforums.org/showthread.php?t=838631")

---

### Post by BewareOfDog on 2008-12-30
My wife's Toshiba laptop sound is all distorted and "echos" the sound. I wonder if this would help it? It only happens when booting into ubuntu 8.10.

---

