---
title: "alsa addresses"
date: 2010-05-11
forum: Hardware
---

### Post by joep-vd on 2010-05-11
I managed to make a multizone mpd-server with pulseaudio, but I'm not so happy with the sound quality of pulse 0.9.14, which is in the 9.04-based distro that I'm running. Sometimes the sound just seem to clip or go on a bit lower volume (though the output levels should not cause this problem). So now I want to try out alsa instead. 

But... I don't manage to find how to call for the different 3.5 mm plugs in aplay. I even wrote a small script to call systematically for all the different devices and sub devices. I only get output on one of the hardware-outputs (and then on all the subdevices). 

With Pulse I successfully sink to these three outputs: 

```

alsa_output.front_Live
alsa_output.rear_Live
alsa_output.front_NVidia

```

I made this list by knitting together some of the info obtained by [FONT="Courier New"]aplay -L[/FONT]. 

The big question is why I cannot 'sink' to the alsa output with alsa, as I can with pulse. Am I overlooking something obvious? Any clues highly appreciated! 

For more info on hardware and alsa-config, see [here]("http://www.alsa-project.org/db/?f=ab61a88af54c92cdf75cddd1409833f8ad3e49f9").

---

### Post by joep-vd on 2010-05-11
Looks like I've solved the pulse glitching issue by following the suggested changes of this guide: 

[http://forums.fedoraforum.org/showthread.php?t=225660](http://forums.fedoraforum.org/showthread.php?t=225660)

I only had to add tsched=0 to all the alsa-sinks, the other suggestion has apparently been adopted by the 9.04 devs.

*edit: But I'm still curious why I don't manage to directly play a wav with aplay???*

---

