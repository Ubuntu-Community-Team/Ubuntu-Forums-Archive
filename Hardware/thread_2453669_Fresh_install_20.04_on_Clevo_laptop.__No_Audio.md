---
title: "Fresh install 20.04 on Clevo laptop.  No Audio"
date: 2020-11-15
forum: Hardware
---

### Post by nvnatz on 2020-11-15
I've got a new Clevo laptop (strictly speaking a Metabox Prime-V) and after trying a couple of distros out, have settled on Ubuntu as it was the only one that was able to get the laptop into an acceptable state.  The only irritation at this point is audio, as in there is none.  I'm dual booting this machine with Windows so I have confirmation that the hardware is operational.

Not having a good understanding of how to get hardware working under Linux, I've been trying out a variety of suggested fixes online.  Sound settings shows "Speakers - Built-in Audio" and "Digital Output (S/PDIF) - Built-in Audio".  When I go to sound settings and run a sound test (against both outputs), I can see the indicators showing that some kind of audio signal is being processed, but no sound (FWIW, I've never seen the "Dummy" audio device).  Similarly, when I speak at the laptop, I can see the audio input indicator showing that sound is being picked up by the built in microphone (haven't tested the recording of audio as yet).

Poking around inside alsa-mixer, pavucontrol hasn't changed things, and tweaks applied to various config files has not altered the lack of sound.

Some (hopefully) relevant info:

```

lspci | grep -i audio
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
01:00.1 Audio device: NVIDIA Corporation TU104 HD Audio Controller (rev a1)

```

FWIW (2) The graphics card driver installed successfully.


Any suggestions?

Cheers.

---

### Post by mastablasta on 2020-11-17
it could be that the sound is out put to HDMI instead of to speakers. in KDE this is easy to check in settings. the settings should have way more options that the two mentioned. there should be stereo, mono, stereo duplex, digital, digital with various number of channels.

also if you have external speakers or headphones you could plug those to their output just to see if it is not sent to headphones. 

Audacity will show even more options to define for output and input. and it can be used to test the mic and speakers.

---

### Post by tea for one on 2020-11-17
> **nvnatz said:**
> I've got a new Clevo laptop (strictly speaking a Metabox Prime-V) and after trying a couple of distros out, have settled on Ubuntu as it was the only one that was able to get the laptop into an acceptable state.  The only irritation at this point is audio, as in there is none.

If the laptop is very new, you may need a later kernel?

Perhaps try a live session using Ubuntu 20.10?

---

