---
title: "Cirrus Logic CS4297A and Skype"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by mr.loco on 2007-07-10
Hey guys, I'm trying to set up Skype and the output ain't working (e.g. i can hear others but they can hear me).

I've checked alsamixer already and it says that both the capture and mic are at full blast and armed to record (if I unmute the mic I can hear Myself speaking).  I tried recording something with the sound recorder as well and all I get is silence. switching between mic1 and mic2 doesn't do anything, and an external mic plugged into the mic port doesn't do anything either. 

Anyone else having the same problem, or even better a solution to it?

Cheers, 
Tom

---

### Post by nothingxs on 2007-08-03
> **mr.loco said:**
> Hey guys, I'm trying to set up Skype and the output ain't working (e.g. i can hear others but they can hear me).

I've checked alsamixer already and it says that both the capture and mic are at full blast and armed to record (if I unmute the mic I can hear Myself speaking).  I tried recording something with the sound recorder as well and all I get is silence. switching between mic1 and mic2 doesn't do anything, and an external mic plugged into the mic port doesn't do anything either. 

Anyone else having the same problem, or even better a solution to it?

Cheers, 
Tom

funny. i have this exact same problem. the thing is that i had somehow solved it before just by running around and changing random things -- it just suddenly started working at some point and i could talk on skype just fine. this doesn't seem to be the case anymore, however, so i would love to know if someone else has a solution to this problem.

seriously. :9

- nxs

---

### Post by nothingxs on 2007-08-03
> **nothingxs said:**
> funny. i have this exact same problem. the thing is that i had somehow solved it before just by running around and changing random things -- it just suddenly started working at some point and i could talk on skype just fine. this doesn't seem to be the case anymore, however, so i would love to know if someone else has a solution to this problem.

seriously. :9

- nxs

i just got it to work right now.

try doing alsamixer -c 0 -V capture, then go all the way to the right to the ADC / DAC settings. set ADC to capture by pressing the space bar. you should be able to record and get skype to work just fine.

---

