---
title: "login problem (stuck with a pink screen)"
date: 2008-07-03
forum: Hardware
---

### Post by stefanos22 on 2008-07-03
Hello,
After unfortunately uninstalling some gstream plugins from synaptic, after the login i am stuck with a pink screen. The cursor moves around fine but there is nothing there besides the pink screen. I tried to hit ctrl+alt+f1 and log from the command line and restore from there the missing files but it didn't work and i steel get the empty pink screen after the login. 
Any suggestions would be very much appriciated.

thank you in advance 
Stefanos

---

### Post by stefanos22 on 2008-07-03
Finally found the file that was missing.
Desktop-base. So if you encounter the same problem just hit ctrl+alt+f1, log in and type sudo apt-get install desktop-base.

---

