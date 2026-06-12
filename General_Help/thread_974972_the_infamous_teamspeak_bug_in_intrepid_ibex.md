---
title: "the infamous teamspeak bug in intrepid ibex"
date: 2008-11-08
forum: General Help
---

### Post by sdwinder on 2008-11-08
Ok so, i have searched hi and low all over google, found many fixes and workarounds for this issue, but none of them specifically for intrepid ibex, probably because its only come out recently, anyway here goes.

As many of you may know teamspeak 2 (voip program) when turned on will work perfectly fine, mic works, playback works, hooray, but one fatal flaw is that it hogs your sound card, no other sound in your system will play, whether its a streaming video, music, or sound inside a game, you get nothing. I am wondering if there is anyway to fix this without having to wait for teamspeak 3 to come out (where we all hope they will use ALSA this time instead of OSS)

I have a Sigmatel POS sound card (half the problem more than likely) 


I have tried messing with the pulse audio driver with no results

I have tried getting aoss (i think thats what its called)

and numerous other fixes to the point where they have all blended into one giant 3 hour waste of my life in which i found around 30 ways of how not to fix the sound in teamspeak.

So, if anyone has intrepid ibex and has found a way to make this work i would appreciate some insight ( i find it funny that i have programs that were not made for Linux that i can run in Linux with crossover perfectly, but programs made specifically with Linux in mind are giving me stupid problems that would sound ridiculous to a pc user 10 years ago.)

---

### Post by kostkon on 2008-11-08
> **sdwinder said:**
> Ok so, i have searched hi and low all over google, found many fixes and workarounds for this issue, but none of them specifically for intrepid ibex, probably because its only come out recently, anyway here goes.

As many of you may know teamspeak 2 (voip program) when turned on will work perfectly fine, mic works, playback works, hooray, but one fatal flaw is that it hogs your sound card, no other sound in your system will play, whether its a streaming video, music, or sound inside a game, you get nothing. I am wondering if there is anyway to fix this without having to wait for teamspeak 3 to come out (where we all hope they will use ALSA this time instead of OSS)

I have a Sigmatel POS sound card (half the problem more than likely) 


I have tried messing with the pulse audio driver with no results

I have tried getting aoss (i think thats what its called)

and numerous other fixes to the point where they have all blended into one giant 3 hour waste of my life in which i found around 30 ways of how not to fix the sound in teamspeak.

So, if anyone has intrepid ibex and has found a way to make this work i would appreciate some insight ( i find it funny that i have programs that were not made for Linux that i can run in Linux with crossover perfectly, but programs made specifically with Linux in mind are giving me stupid problems that would sound ridiculous to a pc user 10 years ago.)
Since you are saying it's using *OSS* (and not *ALSA*), to make it work with *PulseAudio* and thus have concurrent sounds you'll need to run it with the *padsp* utility. This will make this application to send its sound through *PulseAudio* and not directly use the soundcard.

Thus, try running it like this
```
padsp teamspeak
```
or whatever the name for the executable of *teamspeak* is.

If that works, then just change your menu item/launchers for *teamspeak* accordingly.

Hope that helps...

---

### Post by sdwinder on 2008-11-08
unfortunately that is another thing i have tried, it does not work, it still hogs the sound of my system, not to mention my sound coming through to my friends on the other end is very bad, almost impossible for them to hear what im saying.

---

