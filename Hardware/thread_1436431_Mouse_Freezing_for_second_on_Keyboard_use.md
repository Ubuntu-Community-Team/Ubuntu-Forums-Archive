---
title: "Mouse Freezing for second on Keyboard use"
date: 2010-03-22
forum: Hardware
---

### Post by peregrine on 2010-03-22
When I use my computer my mouse locks up for a split second whenever I press a new key. 

So if I press F5 the mouse will not be able to move for about 1ms. This hasn't been an issue until I tried playing Savage. I could move around but my mouse would freeze up for a second.

This happens on any key press. My computer specs are

HP Elitebook 8530w
NVidia Quadro FX 770m 
Ubuntu 9.10(64bit)

The issue is nerve racking as all searches only bring up freezing on standby. I've got no issues otherwise.

---

### Post by brian mcgee on 2010-03-22
Could be a feature designed to prevent accidental mouse clicks when typing. If it's hardware based, there might be something in the BIOS that would allow you to disable that behavior. HTH

---

### Post by peregrine on 2010-03-22
I thought about that, but the behavior is not consistent on Windows 7 or XP. Only on Ubuntu.

---

### Post by brian mcgee on 2010-03-24
Hmm... Not sure why then. Anything interesting in /var/log/Xorg.0.log ? Maybe run the following to find interesting stuff:
```
egrep '!!|WW|EE' /var/log/Xorg.0.log*
```

---

