---
title: "ALSA Codecs Help"
date: 2009-09-27
forum: Hardware
---

### Post by bdormaier on 2009-09-27
I am having problems with my soundcard, specifically if I have my headphones plugged in, it does not mute my onboard speakers.

From running diagnostics on my sound, I know that there are 2 codecs for my laptop(Lenovo Ideapad U350), Conexant ID 5066 and INTEL G45 DEVCTG.

I believe that the G45 is supposed to be for my hdmi and the Conexant for my regular sound jacks.  If I try to adjust sound in alsamixer, the chip that shows is the Intel G45.  This leads me to wondering if maybe my headphone issues are connected with ALSA running G45 over the Conexant driver.

I'm still pretty new to Linux though, so I am looking for confirmation as to whether or not this could be a possibility, and it is, how I'd go about setting ALSA to default to the Conexant codec.

Thanks in advance!

---

### Post by platypus1000 on 2010-02-18
I have the same issue with a Toshiba Satellite T135-1309.  I tried looking at some of the ALSA documentation but didn't get anywhere.  Anyone else have any luck with finding out how to disable one?

---

