---
title: "Laptop mouse button clicking itself"
date: 2012-02-17
forum: Hardware
---

### Post by sarge1238 on 2012-02-17
Hello All,

Apologies, if you feel its a redundant post, but its not.

In my case, I have following configurations:
Dell Inpiron
OS: Ubuntu 11.10
and no external hardware.
I just moved in from Windows to Ubuntu and my machine has both OS

Problem statement: Most of the time I found I got a Left - mouse click at the place where the mouse is currently pointing. in ubuntu and this makes the things messy.
Imagine, you are writing a program and while typing suddenly the cursor moves to other line and the line got messed up.

First i thought its because of my laptop hardware problem, but its not. Because If i log on to Windows i never face this issue, even i type a whole book.

Please help me in resolving the issue.

---

### Post by ajgreeny on 2012-02-17
Are you sure this is not just a case of the touchpad being too sensitive?

See what ```
synclient -l
``` in terminal has to say as it may be possible to set different sensitivity for the various mouse/touchpad actions very easily.

However, I recall reading that being a Dell machine, it is possible that the touchpad is not, and is therefore not detected as synaptics hardware.   It may therefore be much more difficult to overcome this problem, other than disabling it all together, if that is possible, perhaps in BIOS, and then using a mouse.

---

