---
title: "microphone level full scale but no sound Realtek ALC888S"
date: 2017-04-02
forum: Hardware
---

### Post by pete5 on 2017-04-02
Lubuntu 16.10 on Compaq SR5123wm Realtek ALC888S audio. I have a known good microphone connected. If I open the PulseAudio Volume Control and look at input devices microphone port the indicated level is almost full scale even though there isn't much noise in the room. The microphone does appear to be picking up sound because if I tap it the bar jumps a little. If I move the volume control slider down then the indicated level goes down so I can see more range but tapping the mic still only makes it jump a little. If I unplug the mic it drops to zero but when I plug the mic back in it climbs back up and stays there. The level meter indicates the same way it would on an amplifier if there was acoustic feedback from speaker to mic, only in this case there is no acoustic feedback, in fact doesn't matter if the speakers are on or not.

I was trying to use it for Teamspeak3. Other users on the channel say they can hear me faintly and it is very raspy and distorted.

On Windows I'd just open Sound Recorder and see what happens but I don't see any equivalent applet in Lubuntu.

 I know this microphone is good because I have used it before. This is a a dual boot with Windows and I don't seem to have a similar problem in Windows so it would seem the hardware itself is ok.

Driver issue or ??

---

### Post by efflandt on 2017-04-03
I don't know if it is the same problem I have with the microphone in 64-bit Ubuntu 16.10. At first running or switching to Team Fortress 2 knocked out the microphone, so it did not work at all in TF2 voice test. If I unplugged the mic and plugged it back in then it worked for Steam voice test. But today the microphone does not seem to work at all in 16.10. If I bring up Sound Settings under Input, everything under "Settings for the selected device" is grayed out with Input Volume all the way down. Replugging in the mic brings color back under "Settings for the selected device" with Input Volume part way up and Input level moves around when I make noise. But just closing Sound Settings and opening it again, mic volume and Input level are grayed out again. So I cannot do anything with a microphone in 16.10 right now.

If I reboot into 64-bit Ubuntu 14.04 on my other drive, the microphone works fine in TF2 and Steam and Sound Settings. So it is not a hardware problem, it is something gone wrong in 16.10. I have ALC887 audio.

---

### Post by efflandt on 2017-04-14
I got my microphone working in 16.10 by installing **pavucontrol** and playing around with that, maybe by selecting for my microphone "Set as fallback". In any case it seems to work fine in everything now and does not get grayed out in Sound Settings.

---

