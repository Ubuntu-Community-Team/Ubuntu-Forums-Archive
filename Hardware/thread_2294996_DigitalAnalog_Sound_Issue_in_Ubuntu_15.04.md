---
title: "Digital/Analog Sound Issue in Ubuntu 15.04"
date: 2015-09-15
forum: Hardware
---

### Post by Aqui1a on 2015-09-15
Hello,

I've done two fresh installs of Ubuntu because of the following problem, and it's still there. It's driving me up the wall!

Straight from the off, there was no sound being output from Ubuntu. I tested by playing audio files, youtube videos etc. but nothing produced any sound.

I opened Sound Settings to see if I could alter some settings there, but strangely the only device listed in the output pane was 'HDMI / DisplayPort'. I checked the Input tab out of curiosity, and there was *nothing* in that pane at all.

Following this, I then did some extensive searching of the web to try and find a solution, but everything I found - things like reinstalling alsa & pulseaudio and force reloading alsa, checking to see if something was muted in alsamixer, and so on - didn't work.

Finally, I made some progress when I installed PulseAudio Volume Control.

In the Configuration tab of pavucontrol, I was able to select a different profile for the Built-in Audio; I selected 'Analogue Surround 5.1 Output + Analogue Stereo Input (unplugged)'. Doing this appeared to fixboth my sound *and* my microphone issues.

However, once I opened Sound Settings, the sound stopped working. I looked on pavucontrol, and the profile for Built-in Audio had returned to what it was prior, 'Digital Stereo (HDMI) Output + Analogue Stereo Input'.


Does anybody have any idea of how to solve this issue? Is there any way I can add more devices to the Sound Settings device panes, so it's not just 'HDMI / DisplayPort'?

Thanks for your time

Aqui1a


Oh, and I'm willing to provide any information about my hardware if you need it! :)



Update: It's solved. All I did to fix my issue was install Ubuntu MATE, which for some reason detected my internal sound card just fine, and listed it in sound settings devices. I love it!

---

