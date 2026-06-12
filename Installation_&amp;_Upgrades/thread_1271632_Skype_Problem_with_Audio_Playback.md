---
title: "Skype: Problem with Audio Playback"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by anuj27 on 2009-09-21
I am using Ubuntu 9.04. I installed skype and want to have voice chat through it. But whenever i call anyone it shows: [B]Skype won't make calls, "Call Failed: problem with audio playback"

[/B]Please help!

---

### Post by khelben1979 on 2009-09-21
Check your audio settings.

---

### Post by kimberlite on 2009-09-21
Try to use "pulse" option.

---

### Post by anuj27 on 2009-09-21
ya thanx... pulse worked. but suddenly i realised my mic is not working in ubuntu. what can be the reason for it?

---

### Post by khelben1979 on 2009-09-22
> **anuj27 said:**
> ya thanx... pulse worked. but suddenly i realised my mic is not working in ubuntu. what can be the reason for it?

There could be several reasons. One thing to start with is to check the volume meter for the microphone, see attached picture.

---

### Post by kimberlite on 2009-09-22
On Gnome you can configure it under "System" -> "Preferences" -> "Sound" -> "Devices". You may also want to play with ```
gnome-volume-control
```.

---

### Post by mionescu on 2009-09-23
You should *not* select pulse or default device for "sound in" option in Skype.  (Skype 2.0). You can try the other options and hopefully one will work (assuming that the mic is not muted)

---

