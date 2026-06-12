---
title: "No Sound TX2510US"
date: 2009-01-01
forum: Hardware
---

### Post by Kamiyay on 2009-01-01
Sound Card is a RealTek ALC268

I am running Linux Mint, but most of the tutorials I have found regarding this was found here so I was still hoping for help.

I have searched around and still have no sound.

Here is what I did:

installed latest alsa gotten from alsa-project.org
grabbed latest realtek linux drivers and installed them.
added "options snd-hda-intel model=hp" to the end of "gksu gedit /etc/modprobe.d/alsa-base"

alsamixer sees the hardware and none of the channels are muted.
All mixers in gnome are unmuted
Totem and Rhythmbox play the audio and dont complain about the device (but no sound comes out)
When playing a file the "PulsAudio Volume Meter (Playback) registers that things are playing (ie: the bars are moving).

Yet there is no sound. I am at my whits end please help!

---

