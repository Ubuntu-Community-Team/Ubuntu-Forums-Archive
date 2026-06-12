---
title: "HP Compac NC4200 and 8.04 strange behavior"
date: 2008-08-03
forum: Hardware
---

### Post by Frix on 2008-08-03
I have a HP/Compaq NC4200 on which I've recently installed Ubuntu 8.04 "Hardy Heron". Worked like a charm, all devices detected and activated even the wireless network. However, if I run it on batteries and then plug the AC-power back in, it starts to behave quite strange. The GUI freezes every now and then (while the battery is charging) and the laptop is more or less useless during this period. I've examined different log files and from what I can see, it seems to be related to ACPI.

From /var/log/messages:

Aug  3 21:54:16 Frix kernel: [ 1938.652072] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Aug  3 21:54:16 Frix kernel: [ 1938.652932] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Aug  3 21:54:16 Frix kernel: [ 1938.653791] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Aug  3 21:54:16 Frix kernel: [ 1938.654651] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Aug  3 21:54:16 Frix kernel: [ 1938.654655] psmouse.c: issuing reconnect request
Aug  3 22:02:34 Frix kernel: [ 5127.810568] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4

While the battery is charging I get tons of these messages :(
(but as soon as it's back on 85-90% capacity it behaves in a normal way again). 
I've googled the error message, but can't find any solution (more than it seems to be related to ACPI...) 

Any ideas, suggestions what to do?

---

### Post by Cyberponcho on 2009-02-09
Hi Frix, i owe myself a nc4200 (and absolutelly love it!!:D) but i haven't had any problems with it, not a single one, did you make a new 8.04 install? i installed first 7.10 'Gutsy' and after a couple of months i did upgrade then to 8.04 and everything works like a charm, you may have some different pieces of hardware, i got my hardware specs on my [blog]("http://cyberponcho.blogspot.com/2009/02/ubuntu-on-hp-nc-4200.html"), take a look, it may be of help ;)

---

