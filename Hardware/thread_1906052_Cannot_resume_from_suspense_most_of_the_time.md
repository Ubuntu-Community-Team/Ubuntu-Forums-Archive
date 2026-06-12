---
title: "Cannot resume from suspense most of the time"
date: 2012-01-08
forum: Hardware
---

### Post by Walter Bux on 2012-01-08
Hi,

I found a similar problem in this thread [http://ubuntuforums.org/showthread.php?t=1872122](http://ubuntuforums.org/showthread.php?t=1872122), but it seems dead, so I am opening this one. Actually, I have the same experience, my screen is black with a blinking cursor when I resume from suspend, so I have to force a reboot. I actually had „solved“ it for a while with the unexplained trick of setting „export PM_DEBUG=true“ and doing a „pm-suspend“. From then on, resuming worked fine, until it stopped AGAIN. But now, even repeating the aforementioned procedure doesn't restore the functionality.

Also, as I mentioned in the other thread, my TuxOnIce funktionality hangs in the middle of the hibernation (NOT resuming, it cannot resume because it does not hibernate properly). However, when I had supense working for a while, Toi worked, too, and when it broke again, Toi broke again with it.

So there seems to be a connection between suspend-to-ram not being able to go INTO suspension, and Toi suspend-to-disk not being able TO COME OUT of the state.

Any suggestions? For debugging and/or solving?

Many thanks,
WB

---

