---
title: "amarok-xine error - audio output unavailable"
date: 2005-12-05
forum: General Help
---

### Post by BlueNoteMKVI on 2005-12-05
I discovered Amarok when it came installed in Kubuntu, and I love it - but it's driving me nuts.

Initially I left the settings the way they were, using the gstreamer engine.  This worked fine for a while - it was several weeks before I noticed an issue.  I downloaded several mp3s that were ripped at a low sample rate and gstreamer choked on it.  A quick look around the forums suggested I use the Xine engine instead.  I installed amarok-xine and everything was golden for an hour or so, then my music just stopped.  I flipped over to the Amarok window and saw the highlight skipping down then playlist in rapid succession.  When it reached the bottom, I got this error message:
> audio output unavailable - the device is busy
I've tried using various output plugins.  Each one either gave the same error message or crashed Amarok entirely.

I'm running Kubuntu for AMD64.  If this works in 32 bit I'll be switching to that.  I've been fine with the quirks I've seen so far in 64 bit but I need my tunes.

Suggestions?

---

### Post by emuman on 2005-12-05
The problem is propably the switch between stereo and multi channel sound.

See [http://www.ubuntuforums.org/showthread.php?p=455464#post45546]("http://www.ubuntuforums.org/showthread.php?p=455464#post45546")

---

