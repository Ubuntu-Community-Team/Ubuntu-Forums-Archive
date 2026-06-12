---
title: "Ubuntu shuts down, but does not power off"
date: 2009-04-26
forum: Hardware
---

### Post by pixies7 on 2009-04-26
I have an HP DV7 1140eb and have installed Ubuntu 9.04 32-bit (Jaunty)
When I try to shut down, I'm logged off but the my laptop does not power off. When i remove "splash" and "quiet" from the menu.list grub menu, I can see that it blocks on shutting down CPU0.

I have a workaround by powering off my computer via the shell with "sudo poweroff"

---

### Post by antikristian on 2009-04-26
is acpi turned on?

---

### Post by pixies7 on 2009-04-27
acpi is turned off, should it be turned on?

i'm not at my laptop now, but i'll post my menu.lst tonight

---

### Post by antikristian on 2009-04-27
yup, it should be turned on. Acpi sends a signal to the motherboard to shut off the computer completely.

Try to change menu.lst to inlude acpi=on or acpi=ht (most of the acpi services disabled)

---

### Post by pixies7 on 2009-04-27
computer halts with:

CPU1 attaching NULL sched-domain.
CPU0 attaching NULL sched-domain.

but doesn't power off

---

### Post by pixies7 on 2009-04-27
After rebooting the issue is solved, but I have to use the gnome panel Name > Shut Down to make it work. When I close the lid of my laptop, it remains in power on state.

---

### Post by pixies7 on 2009-04-27
Apparently I have to wait a couple of seconds before confirming the shutdown. I have to let the timer countdown for a couple of seconds.

I tried to disable the timer, but then the problem reoccurred. But now it works fine after waiting a couple of seconds.

Thanks for the help antikristian

---

