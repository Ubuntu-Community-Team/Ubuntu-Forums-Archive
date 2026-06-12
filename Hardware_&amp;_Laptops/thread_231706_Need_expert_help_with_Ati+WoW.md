---
title: "Need expert help with Ati+WoW"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by Ookami_16 on 2006-08-07
Hello, I own a ATI RADEON M300, and I have, supposedly, installed it. I type in fglrxinfo and everything comes up fine. However, when I bring up World of Warcraft, the login screen is bearable. Its a little bit choppy but thats ok, its been like that before =/... But the fun starts when i actually log into the game. When it does log in, everything stops, and I can see just the ground and some buildings, but not my character, no trees, some lanterns in the sky... Ya know... The normal thing ='[... Anyway anyone know how to help me with this? Id really appreciate it =]!

---

### Post by sgtBiafra on 2006-08-08
I can't really give ATI-specific advice, but I would think that if you're running this on WINE or a derivative then you would want to run in OpenGL (as opposed to Direct3D) mode.

You should try starting the game with the -opengl option. If that works out OK you can edit your WTF/Config.wtf file and add "set gxApi "opengl"".

**Note:** In the future, threads like this are better addressed in the Gaming Central forum.

---

