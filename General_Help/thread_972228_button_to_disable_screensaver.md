---
title: "button to disable screensaver"
date: 2008-11-05
forum: General Help
---

### Post by jerimiah78 on 2008-11-05
Does anyone know the command to disable/enable screensaver. This one disable`s it.   gconftool-2  –set “/apps/gnome-screensaver/idle_activation_enabled” –type boolean false
How could I get it to enable if disabled, and vice versa

---

### Post by fragos on 2008-11-05
I would think the same command substituting true for false will enable it again.

---

### Post by jerimiah78 on 2008-11-06
i mean more like in one command. Im trying to config a app launcher to enable/disable screensaver. thanks though.

---

### Post by fragos on 2008-11-06
Use gconftool to write a small shell script that tests for state and then toggles true/false. The man pages will show you how.

---

