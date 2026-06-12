---
title: "Pulseaudio plays on screen sound through the microphone"
date: 2010-02-01
forum: Hardware
---

### Post by kadragon on 2010-02-01
I'm having an issue with Pulseaudio where it plays the on screen sound through the microphone.  Whenever I use skype or sound recorder, it captures and plays whatever sounds are being played through my headphones.  Whenever I go to sound preferences and under the input tab I see Input volume (not muted), Input level and Choose a device for sound input.  My sound card is selected.  Under the hardware tab, my Profile is set to Analog Stereo Output + Analog Mono Input.  I get the same if not worse results no matter what I choose.

I ran "alsamixer -V all" in terminal and my mic volume was 0.  After turning it up though; nothing changed.  All other sound levels are turned up too.

System Specs:
OS: Unbuntu 9.10 i386
Sound Card: Soundblaster X-Fi XtremeGamer
Video Card: Radeon HD 4850 (has an onboard sound card that isn't being used)

Everything worked in 9.04, but in there I had many more options in my sound preferences.

---

