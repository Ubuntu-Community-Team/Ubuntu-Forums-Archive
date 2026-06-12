---
title: "Left speaker only on startup"
date: 2008-10-31
forum: General Help
---

### Post by Earl_Maroon on 2008-10-31
When I boot Hardy only the left speaker of my laptop works. The right speaker begins to work when I attach headphones, however. Whether the right speaker is on or off remains the same if I log out then in. In XP on my other partition the speakers work normally.

Does anyone know a solution to this? It isn't a terribly serious problem but it's inconvenient and annoying.

---

### Post by digitalb0y on 2008-11-10
I had a similar issue, Go into your sound mixer.  Check **BOTH** ALSA and the OSS Mixer. For some reason the left Speaker was turned all the way down and it was a easy fix for me.

If you reset it and it happends again then try this script. (for ALSA)

soundon.sh

```
#!/bin/bash
amixer set -c 1 Master 70 unmute
amixer set -c 1 PCM 70 unmute
amixer set -c 1 CD 70 unmute

```

---

