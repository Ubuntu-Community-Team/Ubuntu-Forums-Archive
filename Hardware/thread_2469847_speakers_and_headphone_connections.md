---
title: "speakers and headphone connections"
date: 2021-12-11
forum: Hardware
---

### Post by alain.roger on 2021-12-11
Hi,

I'm trying to have my headphone and speakers connected to my computer at once, so if nobody is at home, I can output sound to my speakers and if someone learns at home, I could use headphone.

My motherboard can output 5.1, so it should be possible to make it work but I do understand how to setup kubuntu to make it work in real life.
Till now I was able to make it only 1 "output system" works...so unplug speakers and plug headphone to have headphone working or the reverse.

Can you help me to avoid to unplug one solution to get the other working ?

thx

---

### Post by CatKiller on 2021-12-13
PulseAudio should automatically switch outputs when it detects that your headphones are plugged in (provided your hardware has the means to detect that something's plugged in, which most modern onboard sound does). Otherwise you could have the speakers plugged in at the back all the time and the headphones plugged in at the front all the time and just chose whether you want to use the front or rear output as appropriate.

Personally, I use the same USB DAC for both, so I can just use the physical volume controls.

---

