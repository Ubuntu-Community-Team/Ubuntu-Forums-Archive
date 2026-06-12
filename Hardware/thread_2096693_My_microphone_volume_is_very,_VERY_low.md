---
title: "My microphone volume is very, VERY low"
date: 2012-12-20
forum: Hardware
---

### Post by TheNavigator on 2012-12-20
Hello there. I've got 2 microphones, internal and external. The internal one works perfectly, but the external one is very low.. I have to get my output volume to the maximum to hear something, and it's not even loud enough.

I've tried all these alsamixer things, got everything I found including mic volume to the maximum, still it was very low. I've even tried searching for a mic boost software, but I had no success with that.

Any help would be greatly appreciated. Thanks.

---

### Post by dannyboy79 on 2012-12-20
within alsamixer, did you check the mic boost setting within the capture tab? what version of ubuntu are you using, do you use pavucontrol (controller for pulseaudio)
also, what software are you using to record and playback?

---

### Post by TheNavigator on 2012-12-20
alsamixer, everything's maxed
pavucontrol, what's that?

The software I use is "Sound Record" thing from Ubuntu, 12.10

Also, I've tried my mic on Windows. It looks like the mic's volume itself is very low. Is there any way to boost it?

---

### Post by dannyboy79 on 2012-12-21
pavucontrol, enter it in a terminal

---

### Post by TheNavigator on 2012-12-21
maximum :|

---

### Post by cwsnyder on 2012-12-21
I think you have a hardware incompatibility with the microphone.  There are so-called Hi-Z and Lo-Z microphones.  The computer input for your external microphone is set for a Lo-Z (or low-impedance) microphone, and if you plug a Hi-Z microphone which is not designed for use with a computer or if it is switchable between Lo-Z and Hi-Z and is switched to Hi-Z, you would get the results reported.  Hi-Z microphones are often used with PAs and (older) external recorders.

---

### Post by dannyboy79 on 2012-12-21
if everything is maxed in alsamixer (capture controls) and input/recording tab in pavucontrol is turned up then I am not sure.

I use audacity to record commentaries and when my mic input is very low, i simply click on a slider and make it louder (must be a gain type effect) prior to exporting out of audacity to a .wav or .mp3 file and the audio is then fine.

---

### Post by TheNavigator on 2012-12-21
> **cwsnyder said:**
> I think you have a hardware incompatibility with the microphone.  There are so-called Hi-Z and Lo-Z microphones.  The computer input for your external microphone is set for a Lo-Z (or low-impedance) microphone, and if you plug a Hi-Z microphone which is not designed for use with a computer or if it is switchable between Lo-Z and Hi-Z and is switched to Hi-Z, you would get the results reported.  Hi-Z microphones are often used with PAs and (older) external recorders.
How can I deal with that then? :|

@dannyboy, That would work, but I use the mic essentially for Skype, so that's a problem

---

### Post by cwsnyder on 2012-12-21
You _could_ buy an impedance matching transformer, but your cheapest route is simply to buy a microphone designed for use with computers.  They shouldn't be any more expensive than any other microphone, but you may have to buy them from a computer supplier rather than a general electronics supplier.  

You could also try using the microphone in the Aux input instead of the Mic input.  The Aux input is for Hi-Z sources.  If this works better than before, the problem is definitely an impedance mis-match.

---

### Post by TheNavigator on 2012-12-22
> **cwsnyder said:**
> You _could_ buy an impedance matching transformer, but your cheapest route is simply to buy a microphone designed for use with computers.  They shouldn't be any more expensive than any other microphone, but you may have to buy them from a computer supplier rather than a general electronics supplier.  

You could also try using the microphone in the Aux input instead of the Mic input.  The Aux input is for Hi-Z sources.  If this works better than before, the problem is definitely an impedance mis-match.
This microphone is bought from a computer accessories supplier actually.. It's designed for use with computers, looks like the company itself sucks.

---

