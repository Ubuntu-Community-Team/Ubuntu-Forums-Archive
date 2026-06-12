---
title: "Command to disable touchpad during boot"
date: 2014-04-29
forum: Hardware
---

### Post by ccmiller12 on 2014-04-29
Okay, so I installed gpointing-settings-devices so I could disable my touchpad. It does disable, but every time I come into a new log in session, the touchpad will automatically be enabled again. I want my touchpad to be automatically disabled as soon as I boot the computer. I figure a good solution is to run a script as system starts up in /etc/int.d. Sadly, I don't know which command shuts off the touchpad. Can anyone help me out?

Cmiller

---

### Post by ajgreeny on 2014-04-29
Make a shell script in your home with contents:-
```
#!/bin/bash
synclient TouchpadOff=1
``` name it **touchpadoff** and make it executable, then point to it in your session startup-applications using the full pathway.

---

### Post by ccmiller12 on 2014-04-29
Thanks, just what I needed :-).

---

