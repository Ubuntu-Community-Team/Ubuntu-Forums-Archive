---
title: "Can't get Skype to work on new Acer laptop"
date: 2009-02-07
forum: Hardware
---

### Post by jedson3 on 2009-02-07
Hi --
I bought an Acer Extensa laptop and loaded it with Ubuntu. Works fine for the most part but when I tried to set up Skype, I could not hear the test call. Tried all the audio devices. Incoming sound is OK. Seems to be only the mic. Don't know what kind of problem it is. Is Acer somehow incompatible with Linux? Have another machine on which Ubuntu and Skype work fine.

---

### Post by Fonsis on 2009-02-09
Please try this:


1. installed linux-backports-modules-generic by going to Synaptic

2. added 'options snd-hda-intel model=acer' to the last line in /etc/modprobe.d/alsa-base

3. Rebooted, and double clicked on speaker icon in system tray. Sliders for headphone volume now appear and external speakers now work. Internal speakers can be muted without affecting headphone volume by using the keyboard volume control.

---

