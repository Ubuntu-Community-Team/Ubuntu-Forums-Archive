---
title: "Master/PCM Volume"
date: 2008-05-11
forum: Hardware
---

### Post by amenotatsujin on 2008-05-11
I have a Compaq Presario, and the sound buttons on the keyboard do not work. The buttons adjust the master volume setting, which does nothing to the volume. I have to adjust the PCM setting to get a volume change. Is there a way to either associate the buttons with the PCM setting, or get the Master Volume setting to actually adjust the volume?

---

### Post by amohanty on 2008-05-12
Right click on the volume applet on the gnome-panel, select Preferences and then select PCM from the list at the lower end of the window.

HTH
AM

---

### Post by stream303 on 2008-05-12
With Hardy, I'm having a bit of trouble with the master volume, although no pcm level issues.

Have you tried running alsamixer in a terminal?  Alsamixer seems to be the most reliable for me at this point until updates come down....

Alsamixer quickie tips:
left - right to navigate
up - down - change levels
M - key - toggle mute/unmute
B - key - balance channel pairs

Normally I leave my pcm at about 75% and use master only.

---

