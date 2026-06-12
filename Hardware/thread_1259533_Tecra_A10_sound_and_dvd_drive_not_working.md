---
title: "Tecra A10 sound and dvd drive not working"
date: 2009-09-06
forum: Hardware
---

### Post by Ginz on 2009-09-06
I have a Toshiba Tecra A10-12z. I installed Ubuntu 9.04 from a Dvd and it is now running parallel to windows xp. But the sound and the dvd drive only work on windows. The only sound I get on Ubuntu is the error beep. I have a Intel HDA ALC268 Sound Card and a DVD Super Multi drive.

If I try to test the sound with ALSA or OSS i get the Message:
[INDENT]audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
[/INDENT]If I test PulseAudio it says it's testing but i don't get any sound.

Does anybody have any solutions to these problems.

---

### Post by Ginz on 2010-01-10
Alright i found the solution in an other Forum. 

For sound fixing I had to append the lines

      alias snd-card-0 snd-hda-intel
      option snd-hda-intel model=toshiba

to the files /etc/modprobe.d/alsa-base and /etc/modprobe.d/options

And the dvd drive started working after updating to karmic koala

---

