---
title: "Getting a Ps/2 Mouse to work"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by astrocrep on 2005-03-29
As the title says, I have a laptop w/ a synaptics tp.  I am using the TP driver, and I have atteched a PS/2 Mouse.  I cannot get the mouse to work.  

However, I noticed in dmesg, when I move the ps/2 mouse I get:

"psmouse.c:  TouchPad at isa0060/serio1/input0 lost sync at byte 1"

Then when I move the touchpad, I get

psmouse.c:  TouchPad at isa0060/serio1/input0 - driver resynched."

Any clues on how to get the ps/2 mouse to work?

P.S.  Theres nothing in bios to help.

Rich

---

### Post by tmowerman on 2005-03-31
Adding second Mouse Howto

[http://madpenguin.org/cms/?m=show&id=887](http://madpenguin.org/cms/?m=show&id=887) 

That link may help

Tim

---

### Post by casablanca on 2005-07-31
I had a similar problem on a Dell Inspiron 7000 - the touchpad was working fine but was detected as ps2, i couldn't get an external ps2 mouse working but solved it by adding 
psmouse proto=bare
to /etc/modules and rebooting.

See [http://www.debianplanet.org/node.php?id=1094&cid=13296](http://www.debianplanet.org/node.php?id=1094&cid=13296)

---

