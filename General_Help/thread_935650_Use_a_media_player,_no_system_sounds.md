---
title: "Use a media player, no system sounds"
date: 2008-10-01
forum: General Help
---

### Post by Dvorakis on 2008-10-01
When I use a media player, somehow my system sounds stop working...but the media player is just fine.
I get this with banshee.

When I go into the sound settings, and test ALSA and OSS for sounds I get this error.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

Any help on how to fix this?

---

