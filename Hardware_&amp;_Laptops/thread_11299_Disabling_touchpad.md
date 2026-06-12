---
title: "Disabling touchpad"
date: 2005-01-15
forum: Hardware &amp; Laptops
---

### Post by NeoChaosX on 2005-01-15
I have a Dell Inspiron 5100 with a Synaptics Touchpad. Said touchpad seems to automatically click at certain points, which is annyoing, especially since I also have a USB mouse I use. Is there a way that I can disable the touchpad so Linux doesn't see it?

---

### Post by NeoChaosX on 2005-01-16
Also, I can't disable it through the BIOS. If was able to I would've done so already. So I have to disable it through the OS.

---

### Post by daniels on 2005-01-16
Run 'synclient TouchpadOff = 1'.

---

### Post by NeoChaosX on 2005-01-16
'Can't access shared memory area. SHMConfig disabled?'

...what does that mean?

---

### Post by daniels on 2005-01-16
Bleh.  Edit /etc/X11/XF86Config-4, and in the Synaptics section, add 'Option "TouchpadOff" "1"'.

---

### Post by NeoChaosX on 2005-01-17
It works!

Much thanks Dan.  :)

---

### Post by dr johnson on 2007-08-27
BTTT, can anybody please tell me how i might completely disable my laptop touchpad on feisty?

---

