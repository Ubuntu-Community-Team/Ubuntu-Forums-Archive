---
title: "Sound preferences hangs"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by Jerryonimo on 2007-09-12
I Googled -- I don't think anyone else has this problem.  I installed ALSA word-for word (at least everything except the lib package, but that shouldn't make a difference), and I tried to test the sound on my system.  So I went into System > Preferences > Sound Preferences, selected "ALSA" for the sound playback, and go the following error as a normal user:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```
The odd this is, as root, I get a window that says "TESTING PIPELINE," and the status bar just hangs there.
Can anyone help me?  Thanks in advance.

---

