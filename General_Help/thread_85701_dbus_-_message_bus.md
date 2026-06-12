---
title: "dbus - message bus"
date: 2005-11-03
forum: General Help
---

### Post by twelvegates on 2005-11-03
In Ubuntu there is a dbus service that is running in my installation.
What is dbus for? Can I switch it off?

---

### Post by Alexander Kirillov on 2005-11-03
[QUOTE=twelvegates]In Ubuntu there is a dbus service that is running in my installation.
What is dbus for? Can I switch it off?[/QUOTE]
It is required - do not switch off.

Explanation: dbus is  a service which allows applications notify each other of various "events". A major use is hotplugging: when you plug in a USB memory key, an icon appears on your desktop - this was made possible by nautilus being notified of the new device, which in turn was done via dbus.

---

### Post by twelvegates on 2005-11-03
Can one list the installed packages that depend on dbus except Nautilus?

---

### Post by Alexander Kirillov on 2005-11-04
[QUOTE=twelvegates]Can one list the installed packages that depend on dbus except Nautilus?[/QUOTE]
Try selecting it for removal it in synaptic - you'll get a list of other packages which depend on it. In particualr, all power management stuff depends on it. 

 But why do you want to remove it? It is indeed an important one...

---

