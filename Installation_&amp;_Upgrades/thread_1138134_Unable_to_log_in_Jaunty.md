---
title: "Unable to log in Jaunty"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by RetroX on 2009-04-26
Yesterday, I recently updated my computer from Ubuntu 8.10 to 9.04.  I get to the log in screen, but once I log in it shows my desktop wallpaper and nothing else on the screen besides the mouse.  Strangely, when I log in under root it starts up and works.  Is there some configuration problem that I can fix to make this work?

---

### Post by Triptol on 2009-04-26
Your profile in your homedirectory is probably somehow broken.

Easy fix: login as root and rename your homedrive:
```
mv /home/username /home/username.old
```

After you have logged in again, you can transfer your documents and reconfigure.

The other way would be to find out what config is wrong and the updating that config. Is better but will take a lot of time :-)

---

