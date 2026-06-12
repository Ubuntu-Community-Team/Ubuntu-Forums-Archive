---
title: "Disper - Primary display has black vertical bar on the right side"
date: 2011-09-24
forum: Hardware
---

### Post by -Shuji- on 2011-09-24
I have an HP Pavilion dm1z running Ubuntu 11.04.  Switching from laptop screen to external monitor has been a problem but with the help of disper, things got better but not perfect.  I use ```
disper -s
``` to switch to the primary or laptop screen but when I do, there is black vertical bar on the right side which covers about 5% of the screen.

The problem appears if I'm using maximum resolution of 1366x768.  If I change the resolution to 1280x768, it's ok.  Hope someone can help.
```
disper -r 1280x768 -s
```Shuji

---

### Post by -Shuji- on 2011-09-24
To fix this, uninstall disper and use Monitor Preferences from System Properties - Monitors to switch between laptop display and external monitor.  If there is a shortcut key to automatically switch between the 2 displays, that would be better.


Shuji

---

