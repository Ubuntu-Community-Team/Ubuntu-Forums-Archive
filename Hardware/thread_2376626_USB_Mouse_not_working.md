---
title: "USB Mouse not working"
date: 2017-11-04
forum: Hardware
---

### Post by joe7dust on 2017-11-04
Dell Optiplex running ubuntu and only the mouse buttons work. The X/Y coordinates never change as if faulty laser but mouse works on 2nd pc. It is a C8639 Dell mouse made by Logitech according to 'lsusb'.

I've tried many workarounds online involving "synaptics" and "xorg" but nothing has worked so far. The other popular suggestion I found did not work either: "modprobe -r psmouse    ;    modprobe psmouse proto=imps"

---

### Post by Autodave on 2017-11-04
Is this wired or wireless?  Have you tried another mouse on this machine?

---

### Post by joe7dust on 2017-11-04
It is wired and Yes. It's the mouse/machine relation not the machine itself or mouse itself. The other PC I used for testing is running Windows so it is likely related to the drivers in linux or something.

---

### Post by efflandt on 2017-11-05
Which Ubuntu version are you running and what shows up in output of lsusb for the mouse? So when you said "Yes" that means that another mouse works on that PC and just not this mouse?

---

### Post by joe7dust on 2017-11-05
> **efflandt said:**
> Which Ubuntu version are you running and what shows up in output of lsusb for the mouse? So when you said "Yes" that means that another mouse works on that PC and just not this mouse?
That is correct. Ubuntu 16 output of lsusb says Logitech Optical Mouse.

---

