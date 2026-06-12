---
title: "Video bug. Report to launchpad?"
date: 2008-07-29
forum: Hardware
---

### Post by wizardfait on 2008-07-29
I have a Compaq Armada M700, and if I boot with the laptop's screen closed, if I go and open it after the login screen comes up, the screen will be a little glitched, so that the image is up and to the left, and wrapped around the bottom. (So if I go up high enough, it'll come up out of the bottom) however, there's also a black bar. It appears to me as though X doesn't fill the video ram correctly if the cover is closed. Anyone else have this problem, and/or anyone know of a solution? (Other than booting with the cover open, obviously?)

By The Way: If I Ctrl + Alt + Backspace to reset X, it will "fix" it.

---

### Post by ModelM on 2008-07-29
After you boot like this, you might take a look at the log file at:

/var/log/Xorg.0.log

This contains all of the startup messages from Xorg & might provide a few clues as to exactly what is happening.

---

