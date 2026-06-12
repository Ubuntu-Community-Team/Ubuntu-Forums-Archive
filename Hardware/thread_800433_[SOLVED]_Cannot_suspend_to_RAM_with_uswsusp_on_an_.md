---
title: "[SOLVED] Cannot suspend to RAM with uswsusp on an Asus M50Sv-A1"
date: 2008-05-19
forum: Hardware
---

### Post by hotweiss on 2008-05-19
For some reason I cannot suspend to RAM on my Asus M50Sv-A1. I tried to follow the generic tutorial here:

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

...without any success.

I tried to add the -force flag in /etc/gdm/gdm.conf with the same negative results.

The only thing that suspend does is log me out.

I'm now worried that my fingerprint reader software could be behind this mess. Any help would be appreciated.

---

### Post by hotweiss on 2008-05-20
Oh boy, suspend to ram and hibernation works out of the box with Ubuntu 8.04. I followed an old Asus guide that included uswsusp.

---

