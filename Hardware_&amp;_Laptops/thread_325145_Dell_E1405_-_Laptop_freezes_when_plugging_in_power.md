---
title: "Dell E1405 - Laptop freezes when plugging in power adaptor"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by tsvim on 2006-12-25
I just finished installing the 64bit version of edgy on my brand new Dell E1405.
Specs are:
Core 2 Duo (T7200)
1 Gig RAM, 120 Gig Sata HD
Video: Intel 945GM

For some reason when I plug in the power adaptor, my laptop freezes. Nothing works except for pressing the power button.

Any ideas?

---

### Post by pandu.rs on 2006-12-25
In terminal type

sudo /etc/init.d/acpi stop

and then try plug in the power adaptor.

---

### Post by holli on 2006-12-30
might be related: [https://bugs.launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/65027](https://bugs.launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/65027)

---

### Post by tsvim on 2007-01-22
Disabling acpi by running /etc/init.d/acpid stop did not work for me. I'll post an update according to the instruction's you posted on launchpad, holli. Seems we got exactly the same problem taking into consideration we run the same machines with the same configurations.

---

