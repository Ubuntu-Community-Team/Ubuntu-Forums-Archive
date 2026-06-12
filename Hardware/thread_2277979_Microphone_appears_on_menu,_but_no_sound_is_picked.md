---
title: "Microphone appears on menu, but no sound is picked up (Asus X550LA and Ubuntu 14.04)"
date: 2015-05-12
forum: Hardware
---

### Post by Mark_Miller on 2015-05-12
Hi y'all!

I've been working with Ubuntu for almost a year now; it's great! This is my first post in the forums, though. Since the beginning, I have not had a working microphone on my Ubuntu side. I've stumbled around the forums looking for a solution, but never found one.

If I open System Settings > Sound, there is an entry on the left for "Internal Microphone (Built-in Audio)", but the Input Level never shows activity. On my Windows partition, the microphone works correctly, so it is not a problem with the microphone itself.

I've heard of some things like Alsa (didn't she have a Disney movie?) but I have no idea where to begin looking for help. So I'm here! Holler for whatever sort of information you need from me.

---

### Post by sandyd on 2015-05-13
Mic may be muted.

Go to terminal, and run ```
alsamixer
```
Check to see if your using the right sound card, if your not, press F6 and select the right sound card.
Then, make sure that the mic input does not show up with a 'MM' at the bottom of the column.

If it is still muted, try to see if pulseaudio has muted it.
Install pavucontrol```
sudo apt-get install pavucontrol
``` and open Pulse Audio Volume Control in the menu. Make sure inputs are not muted and is getting input there.

---

### Post by Mark_Miller on 2015-05-13
As it turns out the mic was muted, so I unmuted it in Alsamixer, but it still didn't fix it. So I downloaded pavucontrol, which didn't help much either. 

I did get some quite strange behavior, though. For example, if I go to the Input Devices tab, "Monitor of Built-In Analog Stereo" has a levels/volume bar that follows the volume of the music that I'm playing, and then "Built-in Audio Analog Stereo" is always very low. When I switch "Port" from "Internal Microphone" to "Microphone (unplugged)", or when I turn down the recording volume, it kills the music.

I switched "Configuration" to Off (for the one with HDMI options only) and then to "Analog Stereo Duplex" for the other option.

---

### Post by Mark_Miller on 2015-05-14
Now, when I restart, there is a chance that the bongos startup sound instead plays this piercing, high-pitched squeal. My friend plugged in his combo microphone / headphones and the microphone automatically piped itself through the headphones. 

I'm still looking for some sort of solution.

---

### Post by Vladlenin5000 on 2015-05-15
Have you checked/tested the volume level, after you unmutted the Mic? Perhaps it's too high resulting in feedback.

---

### Post by Mark_Miller on 2015-05-15
I turned down the mic and mic boost options as well as the internal mic and internal mic boost options, but it didn't help picking up the audio. Is there something present that can rule out feedback as a problem (rather than something that isn't there and therefore might be a issue fixed by having the right numbers or something?)

---

