---
title: "Synaptics Touch Pad not working after Sleep"
date: 2008-05-04
forum: Hardware
---

### Post by craiger316 on 2008-05-04
Hi I have a Gateway laptop with a Synaptics touchpad.  Everything works great until the computer goes into sleep mode. After it awakes the touchpad no loger works.  However, after hibernating it's fine, it's just when it sleeps.

Anyone else have the same problem?  Any solutions?

---

### Post by Zorael on 2008-05-04
What happens if you do this when it's not working?
```
$ sudo modprobe -r psmouse
$ sudo modprobe psmouse
```

edit: I just tried it and lost touchpad-specific features, like the edge scrolling. meh.

---

### Post by Zorael on 2008-05-04
Restarting X works (for me), though then all your open applications will close. It's better than rebooting your entire system, though.

Ctrl+Alt+Backspace.

---

### Post by craiger316 on 2008-05-04
> **Zorael said:**
> Restarting X works (for me), though then all your open applications will close. It's better than rebooting your entire system, though.

Ctrl+Alt+Backspace.

You know, actually I had tried Ctrl-Alt-Backspace and it didn't work for me, I wonder why it works for you?

I can live without edge scrolling actually (from your previous post suggestion) because the touchpad actually has a specific horizontal area designated for scrolling that X seems to just disregard and instead takes over part of the touch pad for scrolling :(

I'll give your other solution a try and see if I can live with it.

---

