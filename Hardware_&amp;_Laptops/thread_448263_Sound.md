---
title: "Sound?"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by Pandemic187 on 2007-05-18
I've noticed this a few times. Sometimes when I install Ubuntu, the sound just doesn't work, and I can't figure out why. I'm on a Compaq v3000T right now, and the sound works for sure in Windows...and it has worked before in Ubuntu (7.04), but for some reason it's not working right now. Anyone know why this happens?

EDIT: I figured it out. I'm using Alsa, and my mixer was showing sliders for master and PCM. What it *wasn't* showing was a slider for PCM-2, which was muted. Sure enough, I had to unmute PCM-2 for it to work. What a dumb problem.

---

### Post by gilgongo on 2007-05-19
Yes, I and about ten bazillion others have had this exact problem at some time or other. Why is it that alsamixer decides to mute things?

---

