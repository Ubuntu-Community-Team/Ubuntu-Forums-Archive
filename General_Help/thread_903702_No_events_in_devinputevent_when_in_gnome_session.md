---
title: "No events in /dev/input/event* when in gnome session"
date: 2008-08-28
forum: General Help
---

### Post by slhommed on 2008-08-28
I'm trying to view events on any input device in /dev/input, such as:

```
sudo cat /dev/input/event8
```
 
When in a gnome session no events are logged to these devices.  If I switch to a terminal ( CTRL + ALT + F1, not a term emulator like gnome-terminal) then the events are logged to the device nodes in /dev/input.

I'm on Ibex Alpha 4 x86_64.

Any ideas?

---

### Post by sahabia on 2010-03-12
Hi,

Later response to anyone having the same problem.

When using synaptics xorg driver, the option GrabEventDevice prevents any other program than X server to grab input from the touchpad (see man 4 synaptics).

Sahabia.

---

