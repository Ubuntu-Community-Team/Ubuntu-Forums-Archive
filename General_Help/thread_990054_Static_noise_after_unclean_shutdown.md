---
title: "Static noise after unclean shutdown"
date: 2008-11-22
forum: General Help
---

### Post by lamego on 2008-11-22
After a recent unclean shutdown I can only get static noise from the speaker.
Sound was playing fine before this event, I have checked alsamixer and he sound is not muted.
From the Live CD the sound works just fine.

Any hints would be appreciated.

P.S.: I do not remember having performed any update when the sound issue started.

---

### Post by hal8000 on 2008-11-22
> **lamego said:**
> After a recent unclean shutdown I can only get static noise from the speaker.
Sound was playing fine before this event, I have checked alsamixer and he sound is not muted.
From the Live CD the sound works just fine.

Any hints would be appreciated.

P.S.: I do not remember having performed any update when the sound issue started.

Ideally you need to state what sound card and chipset you are using, which Ubuntu distribution you use and which desktop you're running.

If its gnome, try system , preferences , sound.
Sound playback has a drop down list and can be set to auto detect, alsa, oss or pulse audio server, and in my case my Intel ICH5 chipset.

You need to try each option in turn, then click on test to see which sound server works with your card. Hope that helps.

---

### Post by lamego on 2008-11-22
After looking the mixer more carefully I noted that PCM level was set to 0.
Fixed.

---

