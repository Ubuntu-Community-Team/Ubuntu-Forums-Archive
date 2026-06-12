---
title: "ASUS Xonar D2 audio conflict"
date: 2008-09-17
forum: Hardware
---

### Post by d0b33 on 2008-09-17
I never had this issue with Ubuntu, but with Kubuntu I'm having a problem with audio playback from multiple applications simultaneously.  My sound card plays back sound fine when using one application but if I'm using the soundcard while playing a movie and try to use amarok for example I get the "xine was unable to initialize any audio drivers" error message.

What is the best way to solve this issue where I am able to have audio played from multiple sources at the same time with the ASUS Xonar D2 soundcard?

---

### Post by d0b33 on 2008-09-18
I'll have a look through this, maybe it will solve my problems...
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Nepherte on 2008-09-18
There's a bug in pulseaudio that, in general, denies access to every other app than the first one that tries to access the sound card. The rest of the applications is denied access. There are 2 possible solutions. The first one is just using alsa directly instead of pulseaudio (system > preferences > sound, change everything to alsa). The second solution involves fixing the bug in pulseaudio. There's a very simply straightforward copy/paste tutorial here (still no reason not to read everthing very carefully though): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I leave it up to you what solution to pick. They should both work. The first one is a lot easier, but then again, you can do great things with pulseaudio if functioning correctly.
__________________

---

### Post by d0b33 on 2008-09-18
Don't think I have pulse audio installed... no options for it

---

### Post by Nepherte on 2008-09-19
It's installed by default in Ubuntu. So unless you removed it yourself, you still have it. To verify you have it installed, you can run this in a terminal:
```
aptitude search pulseaudio
```
If there's an 'i' in front of the package 'pulseaudio' you have it installed.

---

### Post by d0b33 on 2008-09-19
I'm using Kubuntu, I actually installed pulse but could not get it to work so I uninstalled it... maybe I should give pulse another go but all I want is audio to played by more than one application, gmail notify does not notify me if I'm listening to music for example.

---

### Post by Nepherte on 2008-09-19
I'm not familiar with kde, but isn't there a sort of sound preferences menu? Set everything listed there to alsa if available.

---

### Post by d0b33 on 2008-09-19
> **Nepherte said:**
> I'm not familiar with kde, but isn't there a sort of sound preferences menu? Set everything listed there to alsa if available.

Yep, set everything to alsa... thing is in ubuntu I could have sound from multiple apps at once but just not with kubuntu.

Thanks for trying to help out though.

---

### Post by d0b33 on 2008-09-21
OK just figured out it is audio/video players that use the Xine engine that don't allow access to the soundcard when it's in use, if I use a player like noatun I can still use other non-xine sound applications or the system sounds.

---

### Post by markbuntu on 2008-09-21
You need to set xine to use alsa. It is probably using oss which will cause this problem.

---

### Post by d0b33 on 2008-09-22
> **markbuntu said:**
> You need to set xine to use alsa. It is probably using oss which will cause this problem.

In amarok or a system setting? I tried amarok but still the same.

---

### Post by markbuntu on 2008-09-22
You should be able to change it just in Amarok in Settings/Configure Amarok/Engine change the Output Plugin to alsa.

---

