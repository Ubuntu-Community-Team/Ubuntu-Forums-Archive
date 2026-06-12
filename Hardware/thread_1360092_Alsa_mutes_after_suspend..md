---
title: "Alsa mutes after suspend."
date: 2009-12-20
forum: Hardware
---

### Post by 24601oxy on 2009-12-20
I've had a lot of sound problems with this machine, an Inspiron 1420, and this is the most recent. 


With this most recent upgrade to 9.10, my sound only works after a fresh boot. If I put it into suspend, the sound just stops working. It may be possible that somewhere is getting muted, but not any of the obvious places. 

edit1:

OK, I feel dumb. I went into alsamixer in the terminal, and it was muted there. 

Any way to stop it doing that so I don't have to fix it every time?

edit2:

Ok, never mind. That did work one time. But I've just suspended again, and alsa resumed at 100% volume, but no sound. I am very confused.

---

### Post by bartman on 2009-12-30
See this thread: [http://ubuntuforums.org/showthread.php?p=8582039](http://ubuntuforums.org/showthread.php?p=8582039)
Perhaps you have the same issue.

---

