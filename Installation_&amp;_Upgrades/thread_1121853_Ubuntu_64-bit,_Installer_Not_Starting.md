---
title: "Ubuntu 64-bit, Installer Not Starting"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by ToolSHeD on 2009-04-10
Hi

I just recently got a new laptop and I'm trying to install Ubuntu  64-bit on it. The problem is that the after the live cd has booted the installer doesn't seem to work. I start it and wait forever, nothing happens.

An error comes up just as the desktop loads: "Internal Error: Failed to Initialize HAL". Any guesses?

My specs are: 
[LIST]
[*]HP EliteBook 8530w
[*]Intel core 2 duo 2.5 GHz
[*]2 Gb RAM.
[*]ATI Mobility FireGL V5700
[/LIST]

Can anyone please help, I'm stuck with Vista in the mean time...

---

### Post by ToolSHeD on 2009-04-10
Thanks, aren't there slight disadvantages to this method? I would still like to know why it doesn't work the conventional way.

---

### Post by ToolSHeD on 2009-04-10
Ok, I looked at the installer and typed the following into a terminal:
"ubiquity --desktop %k gtk_ui" and got the following error message:
*error: dbus_bus_get: org.freedesktop.DBus.Error.NoSocket: Failed to connect to socket /var/run/dbus/system_bus: socket: Connection refused*

---

### Post by oldos2er on 2009-04-10
Did you run 'Check CD for defects,' or md5sum?

---

### Post by ToolSHeD on 2009-04-11
Yup, and it was fine.

---

