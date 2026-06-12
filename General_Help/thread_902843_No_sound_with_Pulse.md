---
title: "No sound with Pulse"
date: 2008-08-27
forum: General Help
---

### Post by ~LoKe on 2008-08-27
I've been having no sound issues lately except that Enemy Territory never had sound.  I resolved this today by following the instructions [here](http://ubuntuforums.org/showthread.php?t=362231).

This solved my sound problem with ET, but now I have no sound with anything else (Firefox/Flash, VLC, MPD, etc).  The only app unaffected at this point without changing any settings is Rhythmbox.

So...is there a way to make everything work or is it always "this or that"?

---

### Post by tdrusk on 2008-08-27
> **~LoKe said:**
> I've been having no sound issues lately except that Enemy Territory never had sound.  I resolved this today by following the instructions [here]("http://ubuntuforums.org/showthread.php?t=362231").

This solved my sound problem with ET, but now I have no sound with anything else (Firefox/Flash, VLC, MPD, etc).  The only app unaffected at this point without changing any settings is Rhythmbox.

So...is there a way to make everything work or is it always "this or that"?
It sounds like you are having a problem similar to me.When I played a flash video and then tried to listen to Rhythmbox the sound did not work in Rhythmbox. To fix this I did
```
sudo apt-get install libflashsupport
```

---

