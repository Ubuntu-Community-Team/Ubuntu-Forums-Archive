---
title: "Anyway to test optical port?"
date: 2009-12-25
forum: Hardware
---

### Post by Afkpuz on 2009-12-25
Hi guys, I fear my optical audio port may have failed and wondered if there is any utility or process that I could use to test it.  I had been using it before, so I know that I had the settings correct.  I also tried using the coax plug and that didn't yield any sound either.  Any ideas?

---

### Post by chewearn on 2009-12-25
There was a bug in Intrepid (and probably prior/later versions of Ubuntu) where the SPDIF would died for unknown reasons.  There is a launchpad bug report somewhere if you do a good search to find it.

The strange thing is, after it died it would not come back even with a computer reboot.  I got a script written to basically "kick it" to see if it would restart.

```

#/bin/bash

killall -9 pulseaudio
pulse-session

speaker-test -D spdif -c 2 -l 1
speaker-test -c 2 -l 1

```If it works, you should hear a few seconds of white noise from your speakers (both digital and analog, left and right channels).

---

