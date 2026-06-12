---
title: "X loses mouse after switch"
date: 2008-05-29
forum: Hardware
---

### Post by goldmanns on 2008-05-29
Running Ubuntu Hardy, with KVM monitor/mouse/kbd switcher. I'm using evdev driver for mouse since I want it to be able to use all the fancy buttons (Logitech MX500). However, as soon as I switch to other computer it loses evdev driver altogether:

(II) UnloadModule: "evdev"
(EE) Read error: No such device (19, -1 != 24)
(II) Configured Mouse: Off
(II) Configured Mouse: Off
(II) UnloadModule: "evdev"

Of course mouse is not coming back after switching back to Ubuntu box. 

The same setup & config used to work perfectly in Gutsy. Is there any way to fix this issue and stop X from losing the mouse?

---

