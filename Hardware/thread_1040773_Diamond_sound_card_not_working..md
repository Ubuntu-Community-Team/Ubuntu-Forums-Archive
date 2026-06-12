---
title: "Diamond sound card not working."
date: 2009-01-15
forum: Hardware
---

### Post by bluefox815 on 2009-01-15
I've swapped out my sound card of unknown manufacturer with a Diamond 5.1 surround 16-bit sound card.  The old card barely worked, and I had to use an odd jack (blue, not the standard green one) to get any sound.  The Diamond worked flawlessly, but this only lasted for about 2 minutes, when my entire computer froze. I held my power button to restart, and when I logged in, I had lost volume and all other audio control.

I have gone into "System > Preferences > Sound" and tried all the available drivers (I believe they're called drivers, correct me if I'm wrong:  ALSA and OSS, etc.) for all categories.

My options are:
ALSA - Advanced Linux Sound Architecture
OSS - Open Sound System
PulseAudio Sound Server



All three failed with the following error messages when I click "Test":

ALSA:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.

OSS:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

PulseAudio Sound Server:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
(This one causes "Sound Preferences" to stop responding)

So basically, how would I get my Diamond card working with Ubuntu?

---

