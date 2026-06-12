---
title: "Help with SPDIF Output"
date: 2013-11-08
forum: Hardware
---

### Post by xxtoyedxx2 on 2013-11-08
I've searched around a lot over the last few days and every solution I've found so far hasn't worked for me. I'm trying to use Ubuntu 13.10 and I have an Astro A40 headset and mixamp system. No matter what I try I can't get the SPDIF optical output to function. ALSA recognizes it and lists it in my sound settings but I don't get any audio from it at all.

I checked alsamiixer, and when I try to change my audio card in alsamixer I get a Broken Pipe error.

I've isolated the device to hw:1,1 or hw:1,2. Both devices work on SPDIF when using aplay to play a test wav file and neither will work with aplay if the toslink cable is unplugged. I only have 1 SPDIF output port, so it's confusing to me that both devices would work.

Isolating the device to 1,1 or 1,2, I tried adding the following to asound.conf as per this help page: [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) (I tried adding both 1,1 and 1,2 separately of course)

```
[COLOR=inherit][FONT=Monaco]pcm.!default {[/FONT][/COLOR]        
       type hw
       card 1
       device 1 
[COLOR=inherit][FONT=Monaco]}[/FONT][/COLOR]
```

Still no sound from anything except aplay using a test wav.

I'm a linux noob, but I'm sick of windows. I really want to get this resolved. Many thanks in advance for any help provided, even help that doesn't lead to a solution.

---

