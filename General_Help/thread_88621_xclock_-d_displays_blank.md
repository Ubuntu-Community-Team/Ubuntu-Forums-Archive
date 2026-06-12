---
title: "xclock -d displays blank"
date: 2005-11-10
forum: General Help
---

### Post by avc on 2005-11-10
xclock -d displays a blank window. xclock by itself displays the analog clock correctly. How do I get the digital clock to display? I've tried using -fn with some fonts on my Breezy system, but maybe I'm copying the font names wrong. I just copied them from X11/fonts and also trying wildcards like *Bitstream*. Help!

---

### Post by avc on 2005-11-27
Workaround: Before running xclock -d, change the locale to C with "LANG=C". That should get the digital clock to display properly. If anyone figures out a better way (besides recompiling) let me know.

---

### Post by linkunderscore on 2006-01-16
I am having the same problem. I would like to use it in my FVWM config but I can't get it to display properly. 

Can you explain to me how you changed "LANG=C" ? (Im a novice)

---

