---
title: "Random hard-disk thrashing, all sound apps vanish"
date: 2009-11-18
forum: Hardware
---

### Post by hellmet on 2009-11-18
This only happens in karmic and for the past couple of days. I had Banshee, VLC and Hulu.com in firefox. I was browsing these forums, when all of a sudden, everything hangs and the hard disk thrashes away to glory for about 4 minutes. Banshee and VLC close automatically, and the sound on Hulu no longer works. I had to restart PulseAudio to get sound working. 

Today morning, a little thrashing and sound is all scratchy.. no actual sound. Only scratches. Restarting pulseaudio fixes it.

This hard-disk thrashing thing also happens when I play Simcity. Never used to happen on previous versions of Ubuntu. This had made me suspect ext4, but I'm not sure after these recent incidents.

Not sure which log file to view, or how to debug this situation. Any help?

---

### Post by hellmet on 2009-12-22
Still need help on this. Anyone?

---

### Post by hufemj on 2010-01-01
Sounds like the same problem I have. My Dell Latitude D600 is running desktop 9.10 and randomly goes into disk thrashing to the point where the system is hung. Seems to be a progressive thing, starting out with the mouse pointer slow to respond. Then really slow. Then not at all. In the mean time, the disk activity LED is flashing away like mad.

---

### Post by hellmet on 2010-01-02
Exactly. You described it perfectly. I'm assuming it's an EXT4 issue. Reverting to EXT3 is so hard. Format, re-install, blah blah. I've been waiting for a BUG fix in the Kernel updates, but so far, none have come.

---

