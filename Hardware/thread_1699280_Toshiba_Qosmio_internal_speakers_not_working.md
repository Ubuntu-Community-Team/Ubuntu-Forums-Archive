---
title: "Toshiba Qosmio internal speakers not working"
date: 2011-03-03
forum: Hardware
---

### Post by plueken on 2011-03-03
My wife has a Toshiba Qosmio G45 laptop. Due to her old hard drive dying, I just installed a new one along with a fresh copy of 10.10. Initially, the operating system didn't detect her sound card at all, but I was able to fix that problem by updating ALSA using the scripts and instructions here: [ALSA Upgrade Script Redux]("http://ubuntuforums.org/showthread.php?t=1681577&highlight=alsaconf").

Now the system can recognize her HDA / Realtek sound card, and if she hooks up headphones we can clearly hear the sound through them. But the laptop's speakers don't make any sound at all. If we load Windows, everything plays fine. But Ubuntu is unable to play any sound through her speakers, even when just using aplay and bypassing all of the advanced PulseAudio stuff.

I ran the alsa-info.sh file to get an extended overview of her sound system, and this is what came out of it: [http://www.alsa-project.org/db/?f=ecc8e86da99b1d320507c5fbc5320f05e93f184b]("http://www.alsa-project.org/db/?f=ecc8e86da99b1d320507c5fbc5320f05e93f184b").

Please let me know if you have experienced the same thing, or know how to fix this sort of problem. To reiterate: this is a problem with the speakers, NOT the sound card or ALSA driver, and everything runs fine in Windows, so it isn't a hardware failure.

Thanks so much in advance! This has been driving my wife (and me, subsequently) insane.

---

### Post by plueken on 2011-03-04
Any advice at all?

---

