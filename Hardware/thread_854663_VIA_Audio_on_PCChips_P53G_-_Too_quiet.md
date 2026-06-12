---
title: "VIA Audio on PCChips P53G - Too quiet"
date: 2008-07-09
forum: Hardware
---

### Post by herschen on 2008-07-09
I've seen a bunch of posts about "no audio" with this VIA Chipset (VT8237S) but no one seems to have my problem: It's too quiet. I have the volume on the speakers, in the program and in the system all at max and I can still barely here anything. I have Windows on a secondary partition and it works fine.

---

### Post by herschen on 2008-07-09
Success! I just followed the instruction from this post, albeit for Hoary and it worked fine. When I opened alsamixer, the Master Front column was all the way down, so I don't know if it was due just to the changes I made in alsamixer or if the mods to /etc/modprobe.d/alsa-base affected it too.  [http://ubuntuforums.org/showthread.php?t=10672]("http://ubuntuforums.org/showthread.php?t=10672")

---

