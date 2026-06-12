---
title: "sound driver conflict"
date: 2008-11-23
forum: General Help
---

### Post by chaosdesigner on 2008-11-23
hi.

Im having a pretty anyoing problem with my sound drivers in intrepid. The conflict is between my browser and my other media players. For example opera and amarok: I can listen to music all I want, and i can also start the browser, but if i then turn the music off and say watch a clip on youtube, after i want to turn on amarok again it crashes and I have to force quit & destroy the prozess. 

Can somebody help me resolve this sound driver conflict?

---

### Post by beno1990 on 2008-11-23
Open System -> Preferences -> Sound

Set all except "Default mixer tracks" to Pulseaudio sound server, and then Default Mixer Tracks to whichever selection has Alsa player in brackets.

Then log out and in again, and hopefully it'll be solved.

---

