---
title: "Sound issues - sound only works when I reach GDM"
date: 2008-07-09
forum: Hardware
---

### Post by v0idnull on 2008-07-09
I'm having issues trying to get sound working in Ubuntu. I've tried everything I can think of but to no avail.

Sound Card: M Audio Audiophile 2496 (ice1712 sound module)

When trying to test sound with Alsa I get:
v0idnull@statika:~$ gnome-sound-properties
sound-properties-Message: Error running pipeline 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink': Could not open audio device for playback. [gstalsasink.c(697): gst_alsasink_open (): /bin0/alsasink0:
Playback open error on device 'default': No such file or directory]

Everything in the drop down menu in the sound properties window produces no sound and/or that error, EXCEPT when I select ICE1712 Multi. This creates the irritating sine wave. When options like OSS don't produce an error, they claim they are testing, but there is no sound.

Here is some output from a debugging script I took from Alsa's website:
[http://www.psikon.com/~v0idnull/alsa-info.txt](http://www.psikon.com/~v0idnull/alsa-info.txt)

This is a fresh install of Ubuntu with all the latest updates. On a previous install of Ubuntu 8, I followed all the steps in the Comprehensive sound guide on this forum, but to no avail either. The sound card works 100% under Windows so I'm certain this is not a hardware problem. This problem exists both on the SPDIF output of the card and the analog rca outs as well.

Any ideas folks?

edit: I rebooted to enable the Nvidia drivers for my video card, when prompted for the password, I heard the little drum rap sound. However, after logging in, the above issues still apply.

---

### Post by marioallstar on 2008-08-13
I'm having a similar problem. Audio only works at GDM or during a sound test on the audio properties dialog. Even then, only the beeping noise test works--not the sound event tests.

---

