---
title: "gateway m210 no sound!"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by Norehca on 2007-05-17
Im not new to Linux. Ive used it for about 3 years on and off. Iv used Fedora Core mostly. Ive had bad experience with Linux with compatibility issues and i refuse to give up this time. I have a Gateway M210 laptop. Ubuntu (KDE) installed drivers for everything including my sound card which it recognizes as intel. its a Integrated ADI 1981B. I was so excited as everything works absolutely perfect except for my sound, even the audio controls work! Im using ALSA and tried other architectures with no luck. ive looked around here and there and cant find a solution, i hope the people here can help me. any help would be much appreciated.

Note: sound works with neither Kubuntu, Ubuntu, or Debian.

---

### Post by gilgongo on 2007-05-19
I assume you've checked that alsamixer isn't muting something? Run alsamixer in a console and check for anything with "MM" under it (or zero volume).

---

### Post by Norehca on 2007-05-21
oh my god! im so happy ive gone weeks without sound and finally i have it! i never though itd be something as stupid as having to play around with the mixer! thanks so much!

---

### Post by Tegdap on 2007-07-14
I have the same laptop.  I do not have sound either, i checked the mixer and all levels are up.  Nothing muted.  Can you tell me exactly what you did to get sound?  Anyone know of another solution?  Shows up in Hardware information as 82801db/dbl/dbm (ich4/ich4-l/ich4-m) AC'97 Audio Controller.

---

