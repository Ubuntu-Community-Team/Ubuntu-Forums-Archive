---
title: "Acer Aspire 5520:  Microphone troubles, alsa 1.0.17 strangeness"
date: 2008-08-24
forum: Hardware
---

### Post by Eleaf on 2008-08-24
Hey there.  I'm having some troubles with sound on my acer aspire 5520.
I cannot get the microphone working correctly

I installed Hardy Heron 8.04.  First alsa 1.0.16 was installed.  The volume was really low and even with everything maxed (pcm, main, etc.), the volume was perhaps half of that on windows.  The integrated microphone *worked* but was so quiet you couldn't really hear anything except tapping or screaming right into it (and even then there was almost no signal).  I had the internal mic boost volume slider up and fiddles with all the other sliders.

So I installed alsa 1.0.17 from this installation script:  [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959) .
Not sure if it's necessary but I also ran the commands to compile the modules:
```
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

```

I rebooted and alsa 1.0.17 seems to be running, the volume wasn't any different so I added ```
options snd-hda-intel model=acer
``` to /etc/modprobe.d/alsa-base .

I believe the sound is a little bit louder, but now the audio scrollwheel on the side of the laptop adjusts the pcm volume not the master volume.  (I'd like to just set the pcm and have the scrollwheel control master volume.

The microphone is not working at all.  Input source is set to front mic and I fiddled with all the volume sliders, but absolutely no sound is detected from the internal mic input (I tried vusliders and audacity).

Could anybody add some inspiration to get both the scrollwheel volume (which was working correctly before) and microphone to work correctly?

Perhaps I need to downground to alsa 1.0.16 and add the snd-hda-intel model=acer line, because microphone was at least sortive working before.

Thanks!

---

