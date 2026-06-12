---
title: "A few probably connected sound issues"
date: 2016-02-02
forum: Hardware
---

### Post by plkoij on 2016-02-02
I broke my headphone jack a few months ago and bought a USB audio adapter. Often, it works totally fine: I just plug it in and select it in the sound output list. I also need to use a workaround for getting sound to come out of the speakers; I use hdajackretask to override the broken headphone jack to "Not connected." 

Sometimes, when I wake up the computer, the sound output list is empty and I have to start pulseaudio  manually. This is not a big deal, I'm just throwing it in in case it's related to my other problems.

The biggest problem is that sometimes the sound output list is empty and starting pulseaudio doesn't fix it. When this happens I have to restart the computer.

Another problem is that sometimes when I try to override with hdajackretask, I get the error message "tee: /sys/class/sound/hwC1D0/reconfig: Device or resource busy." Other times I get a message that it can't stop pulseaudio from respawning. In the latter case, I can just manually kill pulseaudio, but I think this might be correlated with the sound output list going empty.

It looks like no sound cards are showing up when I run "aplay -l"

Most of the suggested sound card fixes I've seen have been for when the sound card never works. If anyone has any ideas why it might stop working like this, it would be greatly appreciated.

---

