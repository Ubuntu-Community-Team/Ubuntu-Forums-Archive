---
title: "Trouble with microphone and SB600 Azalia"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by jeff_p on 2007-10-09
Hello everyone,

I am having trouble getting the microphone on my Inspiron 1521 to work.  It is an SB600 Azalia soundcard.  I am running xubuntu Feisty, the x86-64 version.

I have the rest of the audio working well...the speakers and the headphone jack, that is.  No complaints there.  The mic, however, does not give any input.

I'm not sure that this is a hardware problem.  When I to turn "capture" or "capture1" up, they immediatly go back down to 0.  I can turn them up in alsamixer and they stay up, but there is no change in the input..I am testing this using Audacity, trying each of the inputs available.

Can anyone think of some problem that would cause those inputs to shoot down to 0, after turning them up?

---

### Post by ccarpita on 2007-10-23
I have a Dell 1521 w/ the SB600 Azalia card, and I had precisely the same issue, which I resolved successfully.

The ALSA drivers that you currently have are probably 1.0.13.  You need to upgrade to the current stable version, 1.0.15.

First, I tried 1.0.14 and lost all sound, and I couldn't successfully modprobe the driver, so you probably don't want to use that one ;)

You can download the drivers here: [http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

Or use these quicklinks:
[alsa-driver-1.0.15]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2")
[alsa-lib-1.0.15]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2")
[alsa-utils-1.0.15]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2")
 
Now, go to [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and follow, verbatim,  the instructions under "Update to the Latest Version of ALSA"

Hope this works for you too!

---

