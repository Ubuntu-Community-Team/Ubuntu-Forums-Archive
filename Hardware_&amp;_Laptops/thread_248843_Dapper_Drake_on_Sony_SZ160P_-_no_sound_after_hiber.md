---
title: "Dapper Drake on Sony SZ160P - no sound after hibernate or standby."
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by mute1 on 2006-09-01
Hi all,

This is the first Linux distro I've tried thats given me 99% functionality from the install. I'm new to Linux and predicatably have a question. 

I guess I'll list what isn't working since the list is far shorter.

I can hibernate, and standby the laptop without any trouble, but when I resume the sound seems to quit working. Is there a way for me to reinitialize the sound server after a hibernate or standby?

Cheers!

---

### Post by mute1 on 2006-09-02
So nobody has any ideas?

---

### Post by fidel10 on 2006-09-03
I'm new to Ubuntu too. I think you have to edit /etc/default/acpi-support. there you may add some modules to restart after hibernate. Unfortunatly you have to find out their name (I can't help you in that case)

---

