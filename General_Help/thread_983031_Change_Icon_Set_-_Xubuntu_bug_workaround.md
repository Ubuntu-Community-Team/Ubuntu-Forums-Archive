---
title: "Change Icon Set - Xubuntu bug workaround"
date: 2008-11-15
forum: General Help
---

### Post by wendigo10 on 2008-11-15
On my Xubuntu Hardy, I have a weird bug - when I change the icon theme the icons in Thunar and Firefox are the Rodent icons - they simply don't change. :(
The solution to the problem is quite simple : rename the Rodent folder to something else so it doesn't find the Rodent icons. :)

Execute in terminal -
```
sudo mv /usr/share/Rodent /usr/share/Rodent1
```

Then logout or restart (or restart X) and see the difference. If the problem persist, change the icon theme to something else (e.g Human) and back to your favourite set. :popcorn:

---

### Post by morgengenuss on 2008-11-15
isn't that a question of what you define as a fallback-theme in your "index.theme"?
(i'm talking about the "Inherits=Tango,gnome,hicolor" setting)

---

