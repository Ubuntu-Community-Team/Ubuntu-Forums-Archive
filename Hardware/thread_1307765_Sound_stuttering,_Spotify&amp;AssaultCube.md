---
title: "Sound stuttering, Spotify&amp;AssaultCube"
date: 2009-10-31
forum: Hardware
---

### Post by applecake on 2009-10-31
Hey!
I have a HP dv5-1103el laptop. In 9.04 I had no sound at all, but now in karmic I have. The sound works perfect in for example Rhythmbox, stutters nothing or very, very little.

But when I run Spotify through WINE the sound stutters in the beginning of the songs, runs fine for some minutes, and then it stutters all the time, making it impossible to hear anthing till the next reboot. I have looked in [this thread]("http://ubuntuforums.org/showthread.php?t=1304988") and followed the tip there to update to wine 1.2, so before I could only listen for 2 minutes and then nothing.

Also, I've downloaded AssaultCube by tar.bz2, and fixed a graphics issue, but from time to time, the sound stutters and eventually gets replaced by "buzzy" sounds, got a .ogg if you want to hear.

My lspci prints two devices:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]

/applecake

---

### Post by applecake on 2009-11-01
*bump*

---

### Post by HaguMe on 2009-11-07
Hey, same here...

I thought it was the sound driver, then I switched from alsa to OSS, but it's still with those horrible noises sometimes.

I hope someone could help us, at least we're two with the same problem.

Greets.

---

### Post by jack0rlando on 2009-11-09
Same Here. I think it to do with SDL Games. I fixed the spotify problem by switching to the Esound driver in wine. Worked perfectly but games like assault cube still start up with a fuzzy sound and eventually fix themselves.

---

### Post by jack0rlando on 2009-11-16
Ok I think I have completely fixed the problem. It was to do with Openal which all my games were using. just download the latest version 1.9563 from here [http://ftp.aarnet.edu.au/debian/pool/main/o/openal-soft/](http://ftp.aarnet.edu.au/debian/pool/main/o/openal-soft/) and all your problems should go away. Worked for me and now I can game on ubuntu once more!

---

