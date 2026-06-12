---
title: "I have a Lenovo Z585 IdeaPad, normal shutdown-not working?"
date: 2013-05-14
forum: Hardware
---

### Post by D1Knight on 2013-05-14
Hello. As in title, my puter is a Lenovo Z585 IdeaPad. I have added to the kernel options, acpi=off, via the boot-repair tool. This was done, because the boot up would just hang. I am on Ubuntu 12.04.2 64 bit. When I attempt a "normal" shutdown, my screen shows the splash screen (almost there), but hangs. I have to do a manual/hard shutdown (hold power button for 5 seconds).:(

I have used this idea from another thread in this forum: edit /etc/modules/ as root with text editor at bottom of the list.
```
apm power_off=1
``` Then reboot after saving.

This for me did not change anything. Any good/sound advice, is appreciated.:)

---

### Post by D1Knight on 2013-05-28
*Bump*

Anyone...anyone??

OK, looks like I am having an even bigger issue, shall post another thread in hardware section.

---

