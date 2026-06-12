---
title: "Speaker Failure"
date: 2008-08-06
forum: Hardware
---

### Post by yanom on 2008-08-06
My speakers will play sound when i go to System>Administration>Hardware Testing, but not anywhere else. why is that?

---

### Post by loboc on 2008-08-06
ALSA might be working but maybe there is a sound daemon That is not functioning 

Preferences>Sound> and change your outputs from ESD or PULSE to ALSA 

Or look into how to get pulse running it might be as simple as adding /usr/bin/pulseaudio to your session

>Preferences>Session

---

