---
title: "Ditched Pulseaudio - now I have no hardware volume control?"
date: 2010-01-12
forum: Hardware
---

### Post by detroit/zero on 2010-01-12
I just finally got around to ditching the disaster that is Pulseaudio in my Karmic install. 

Everything works the way it should: I have good sound, no more audio glitches during media playback, and, believe it or not, my whole desktop seems snappier and more responsive.

Problem I'm having is that the hardware volume control knob on my laptop no longer works. 

Before the Pulseaudio Plague was unleashed on the Ubuntu world, there was a volume control applet that lived on the panel. You could control the system volume from this applet, but if you right-clicked on it, it would bring up a window with various options for adjusting the levels of the various tracks (Master, PCM, Front, Mic, Mic Boost, etc..). From the preferences dialog inside *gnome-alsa-mixer*, you could select the default track that your hardware control would operate. The preferences dialog in *gnome-alsa-mixer* no longer provides this option, and I'm stuck with my hardware control being tied to a track that doesn't effect volume levels, and having to use the volume applet that comes with Avant Window Navigator.

Can someone tell me a way to get my hardware control back? Is there a setting in gconf or a file I can edit somewhere?

---

### Post by detroit/zero on 2010-01-13
Bump.

---

### Post by Yellow Pasque on 2010-01-14
Get the gnome packages from here: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)
If you add the PPA to your sources, don't install the portaudio or (lib)canberra stuff from it, as they're meant for OSS/4 users.

---

### Post by detroit/zero on 2010-01-14
Worked like a charm, thanks!

---

