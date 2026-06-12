---
title: "GDM Font size."
date: 2008-08-06
forum: General Help
---

### Post by Christopher.Sean.Bailey on 2008-08-06
Hey everyone! I recently switched monitors and decided to use a higher resolution. Everything is working fine within Ubuntu itself but the login screen (Gdm?) displays font's so small that they are unreadable. I read through a few similar posts but was unable to fix the problem. If I switch back to my 17inch monitor with a resolution of 1280x1024 everything is fine but On my 26inch LCD at 1368 x 768 the problem persists. Any help would be appreciated.

---

### Post by pauper on 2008-08-06
In order to change Greeter window fonts you need to edit an XML file of that
particular theme:

```
gksudo gedit /usr/share/gdm/themes/<theme_name>/*.xml
```

Look for font=" " values and change them to appropriate.

---

