---
title: "rolling back unsuccessful alsa driver installation"
date: 2008-12-05
forum: Hardware
---

### Post by korihor on 2008-12-05
Hey,

This is about my Samsung NC10.
The speakers work out of the box, but the headphones don't turn off the speakers. To solve that problem installing the latest alsa drivers is an accepted fix (even worked for me on Fedora):
[https://help.ubuntu.com/community/NC10#Audio%20-%20Alsa%20Driver](https://help.ubuntu.com/community/NC10#Audio%20-%20Alsa%20Driver)
Those directions were incomplete so I followed the more full ones here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I've tried this several times on several installations with several different configurations on the ./configure script, but each time after reboot sound is BARELY audible (you have to put your ear on the speaker).

Any idea why it's not working for me but works for others (and for me on Fedora)?

And while we're at it, how do I roll back these drivers to use the ones Ubuntu came with, at least as an intermediate solution?
I added the following to /etc/modprobe.d/blacklist but it did not work:
blacklist alsa-driver
blacklist alsa-lib
blacklist alsa-utils

Thanks for your support!

---

