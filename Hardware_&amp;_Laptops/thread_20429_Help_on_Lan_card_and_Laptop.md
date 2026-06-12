---
title: "Help on Lan card and Laptop"
date: 2005-03-16
forum: Hardware &amp; Laptops
---

### Post by ptsenior2000 on 2005-03-16
I recently aquired a Laptop from a friend and installed Ubuntu version 4.10 from a cd packaged with Linux User/ Developer.  The install went great, but I have a residual "X" like the X Windows cursor in the middle of my desktop.  Is there a way to remove this?  My mouse works fine, but the "X" is still there.

Also, I could not get it to recognize my pcmcia network card.  I looked on the driver support page and it says the drivers should load automatically.  The driver is 3c574_cs .  The actual device is model: 3CXFE574BT.

Note: The installation told me there was no network card detected.  Should I do a modprobe or insmod?

Thanks in advance for any help.

---

### Post by ptsenior2000 on 2005-03-17
Update: Ok, I did some research and installed linux-686 in order to solve the problem.  This version seems to have the drivers as I did a modprobe and it worked.  However, the system still does not see my card.  I looked into modinfo and sure enough, the driver is there under pcmcia and pcmcia-core.  I tried an insmod -f, but the insmod couldn't find the file.  Is there something conflicting here?  Or maybe I'm missing something?

---

### Post by LadyRoot on 2005-03-31
Turn acpi off, will work.

(in lilo.conf add "append=acpi=off" if you are using lilo).


greetings

---

