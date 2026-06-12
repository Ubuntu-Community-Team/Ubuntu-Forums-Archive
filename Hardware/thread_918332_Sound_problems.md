---
title: "Sound problems"
date: 2008-09-12
forum: Hardware
---

### Post by Zerok60 on 2008-09-12
I try to listen to something but I get no sound. I used cat /proc/asound/card0/codec#* | grep Codec:


Codec: Generic 11c1 Si3054
Codec: Realtek ALC861

---

### Post by knattlhuber on 2008-09-12
Just a couple of shots in the dark:
Have you checked if all the sliders in your default mixer in System > Prefs > Sound are up to the max and no channel is muted?
Have you tried changing the default mixer?
Are the sound devices set to Autodetect?
Do you have no sound as in 'no sound at all'? Or is it just very very low? In the latter case, you could try installing gnome-alsamixer and cranking up the sliders for the surround sound.

---

