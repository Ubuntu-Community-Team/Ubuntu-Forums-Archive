---
title: "installed kde with gnome and now have issues with audio"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by mickcalcara on 2008-12-06
Hello,

I have Intrepid Ibex installed with the gnome desktop. Performance has been great however,I installed KDE and now have issues with the audio. For example:  If I go to the sound preferences and perform a "Test" under system sounds I get the following:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

If I change to ALSA and do a test I get

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

Thanks for any help.

---

### Post by inobe on 2008-12-06
okay, you now have kde installed, what version ?


what tutorial did you use ?


please provide as much information as possible, otherwise we will be assuming !

---

### Post by mickcalcara on 2008-12-06
Thanks for the reply.. It is KDE 4.1  This is the howto I followed: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) to install KDE.

---

### Post by mickcalcara on 2008-12-06
bump

---

### Post by inobe on 2008-12-06
have you configured adept for updates ?

i did something similar and needed to configure adept and add kde repos to fix some problems.

---

