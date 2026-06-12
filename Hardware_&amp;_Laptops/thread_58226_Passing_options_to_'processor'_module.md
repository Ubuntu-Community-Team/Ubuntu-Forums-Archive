---
title: "Passing options to 'processor' module"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by infinito on 2005-08-19
Hi everyone!

I'm owner of a HP nx8220 laptop, which has a little problem with high-pitch-noise, which seems to appear as well on some IBm laptops.

The solution is to tell 'processor' kernel module nor to allow cstate 4, so something like "insmod processor max_cstate=3" works.
The problem comes when i try to tell ubuntu to load this module with that option.
I tried to:
- add "processor max_cstate=3" to /etc/modules -> Nops
- add "options processor max_cstate=3" to /etc/modprobe.d/hp.modprobe -> Nops
- add "options processor max_cstate=3" to /etc/modutils/hp.modutils -> Nops
- add "options processor max_cstate=3" to /etc/modprobe/alias -> Nops
- add "processor.max_cstate=3" to options on /boot/grub/menu.lst -> Nooothing

Anyone can tell me howto make this work?? The only way i found was doing:
# echo 3 > /sys/modules/processor/parameters/max_cstate
But i don't like this method...

Any idea???
Thanks!

---

