---
title: "it keeps on crashing"
date: 2008-07-25
forum: General Help
---

### Post by DivinityX on 2008-07-25
I'll be on UBUNTU just surfing the web and listening to music when BOOM, either one of three happens...

1) All freezes except for mouse. (I let it sit there for half an hour, nothing)

2) Screen goes black, sound stops.

3) Restarts itself without warning.

I have 3 hard drives two run windows and the other runs UBUNTU & UBUNTU Studio. My guess is i've made some foolish downloads on windows and got a virus witch is causing it. (windows crashes the same as UBUNTU) although i think that's a little out there...

System info:
CPU: 3 GHz
RAM: 1 GB
Video: 512 MB (i think)
Free space: a couple of MB on primary
I've used the special effects sometimes but it still crashes no matter what...

Can someone help me?

---

### Post by Dylock on 2008-07-25
Hmmm, if its crashing both windows and ubuntu I would say its a hardware problem. My first inclination would be to check that your cpu isnt running to hot. You can do this in windows via the program speedfan (I'm sure there are others) or you can use lm-sensors in ubuntu (you can find a guide on how to install this on the forums somewhere, it usually is a matter of running sensor-detect and answering yes to the questions). 

A virus on windows shouldnt be effecting anything your doing on ubuntu unless  1) ubuntu is running something on a wonky windows partition or 2) something is up with the boot sector. Both seem kind of unlikely so I don't think this is the cause.

Also only keeping a few MB of space free on your HD is not a good thing, might want to clear up some space.

Does the problem happen only when you listen to music, or only when you do some certain task? Also you might check your log files and see if you can see anything going on there around the time of the crash.

---

