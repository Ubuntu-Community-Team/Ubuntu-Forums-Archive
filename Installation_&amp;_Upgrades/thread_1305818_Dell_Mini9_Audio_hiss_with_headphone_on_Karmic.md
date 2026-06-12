---
title: "Dell Mini9: Audio hiss with headphone on Karmic"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by fedleo on 2009-10-30
I'm opening again this thread because the karmic koala forum now is closed and no one can reply...

When you put headphone jack in an hissing sound starts from speakers, if you remove headphone the noise stops immediately. The sound in headphone is quite perfect.
I'm on a Dell Mini9 dual boot machine (9.04 and 9.10), with jaunty with kernel 2.6.28 sound is perfect with no issues. Audio settings are the same on both OS (done with alsamixer). I suppose it's a pulseaudio/kernel settings related problem (Karmic now uses 2.6.31-14 kernel) but can't be sure.
Tested it with mics muted and all audio set to zero. No luck.
lspci reports:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Could someone confirm this issue on Mini9 before I start a bug on launchpad?

Thanks.

---

### Post by mzilhao on 2009-11-06
hi,

i don't have a dell mini, but i'm experiencing the very same issue.
there's a hissing sound coming from the speakers when i plug the headphone jack.

my specs:
Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

this also happens with the Karmic Live CD. i've also tried with everything muted, and no luck...

any ideas?

cheers

---

### Post by aamir.nedian on 2009-11-11
I can also confirm the same issue. I recently upgraded to Karmic on my Toshiba Satellite and there was no such issue with Intrepid or Jaunty. At first I thought that this issue was due to upgrading Jaunty to Karmic so I made a fresh new installation of Karmic but the issue persisted. I believe this has something to do with the new sound mixer in Karmic. Below is the description of bug as experienced by me. 

The hissing starts a few seconds after the sound system is idle, 7.5 seconds to be exact. Hissing stops immediately and completely if there is any sound output even as short as "beep -l10" or if any sort of activity in sound mixer even just opening it from the panel. Wait another 7.5 seconds and the hissing starts again. Strange enough, the hissing also comes from the built-in notebook speakers as well as the headphone when it is plugged in. But the sound output comes only from the headphone as expected.

---

### Post by fedleo on 2009-11-11
Bug opened on [launchpad]("https://bugs.launchpad.net/ubuntu/+bug/480929").

Please add any additional information here, thanks!

---

### Post by mzilhao on 2009-11-15
i've added my information to the bug report.
i found a partial workaround, by following the suggestions from this thread:
[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)
see the bug description for more info...

---

