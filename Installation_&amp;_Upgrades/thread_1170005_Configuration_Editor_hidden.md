---
title: "Configuration Editor hidden"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by artsci2 on 2009-05-25
Add/Remove Applications shows that a program, "Configuration Editor" is installed on all ubuntu systems I'v ever used. Yet I have never been able to find that program. Where is it and how do I srtart it?

---

### Post by drs305 on 2009-05-25
You may be referring to gconf-editor:
```
gconf-editor
```
If you want to change root/universal settings, start it with "gksudo".

It allows you to set a large variety of preferences. Drill through the folders to see what's available. Two subfolders of "apps" containing popular settings that are often tweaked are "metacity" and "nautilus".

---

### Post by Tibuda on 2009-05-25
Press Alt+F2, type gconf-editor, hit enter. It is something like windows registry.

EDIT: nevermind

---

### Post by presence1960 on 2009-05-25
On Jaunty do this System > Preferences > Main Menu. In System Tools check Configuration Editor. Close Main Menu window. It will now be under Applications > System Tools.

Of course you can use a terminal as suggested above. Your choice.

---

