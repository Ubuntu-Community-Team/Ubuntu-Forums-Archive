---
title: "acpi laptop mode?"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2007-02-13
i have enabled "laptop mode" in the acpi settings of /etc/defaults/acpi-settings

and now my hard disk spins down after a few seconds of inactivity.
is this all laptop mode is? does it do anything else? can i keep whatever else it does and stop it from spinning the hard disk down?

thanks.

---

### Post by ltmon on 2007-02-13
I'm pretty sure it is only tweaking the hard disk behaviour and no more.

---

### Post by luopio on 2007-02-21
I just installed "laptop-mode" and went through /etc/laptop-mode/laptop-mode.conf. There you can see that laptop-mode can handle a lot of other things as well. There you can also control the spinning behaviour. 

Stopping the spin-down-feature would probably extend your laptop HDDs life, but what use could it be without it?

---

