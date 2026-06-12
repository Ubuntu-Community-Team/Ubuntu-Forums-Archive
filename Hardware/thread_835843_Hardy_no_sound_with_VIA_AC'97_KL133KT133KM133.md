---
title: "Hardy no sound with VIA AC'97 KL133/KT133/KM133"
date: 2008-06-20
forum: Hardware
---

### Post by whizkid515 on 2008-06-20
I recently installed Xubuntu 8.04 on my 7-year-old HP Pavilion XT936. The installation is working wonderfully, except I have no sound. The computer has a VIA KM133 (very similar so KL133/KT133), with an AC'97 audio codec (not as in MP3, if you don't know what codec means in this case). I have unchecked "External Amplifier" under my Volume Control properties, which was a common fix listed on some website I visited on a Google tangent. I really would like to have sound, or at least disable that really annoying system beep that plays instead of a sound file. Also, I noticed that my Network Settings are unconfigureable under Network Settings. I don't think this is related, but I would like to be able to configure them.

---

### Post by whizkid515 on 2008-06-21
Okay, my sound is working. It actually was all along, I just didn't notice because no system sounds were being played, only the beep was. Anyone know how to enable the system sounds instead of the beep being played???? This is urgent, and I hate to be a jerk, but it is really annoying having the beep sound being the only sound played by the system!!!

---

### Post by Odrodzona-Sarmacja on 2008-06-21
Install Alsamixergui with synaptic manager.

---

### Post by whizkid515 on 2008-06-21
> **Odrodzona-Sarmacja said:**
> Install Alsamixergui with synaptic manager.

Um, I did?

That's not helping. I can get sound, I streamed a music file off Skreemr, no problem. It's just that first of all, there are no sounds at all in /usr/share/sounds, and second of all, this is causing the system to beep instead of playing the missing sound files.

---

### Post by whizkid515 on 2008-06-21
Oh, by the way, ALSA Mixer reports my card (really a codec) as a Via 82C686A/B rev20.

---

### Post by Odrodzona-Sarmacja on 2008-06-22
Your players and you system are configured to use Alsa driver too?

---

### Post by whizkid515 on 2008-06-22
> **Odrodzona-Sarmacja said:**
> Your players and you system are configured to use Alsa driver too?

Wait... what? Well, lets see, audio played fine from firefox and skreemr (flash), so I'm guessing, yeah. I just need to get my computer configured to play system sounds. That's it. Instead of that, it plays a really annoying beep sound. It's not that my sound isn't working, I think my sound files are missing. My sound actually works perfectly!

---

### Post by Odrodzona-Sarmacja on 2008-06-23
It looks like you are missing some sound system program to set music instead of beeping. I searched in synaptic manager with "sound system" and I got two interesting to you maybe programs. One "softens" the peep from computer by sending it to sound card instead and kde program "arts", which is kde sound system. I think you need to look into synaptic manager and search after "sound" and see if you don't need to install something additional to enable this functionality on Xubuntu.

Good luck!

---

