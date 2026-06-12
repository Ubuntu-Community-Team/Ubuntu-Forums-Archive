---
title: "Making devices readable"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by tommie-lie on 2005-12-03
Hi community!

I'm very close to getting my MX3000 multimedia keyboard to work (don't worry, I will publish a detailed description shortly). There is only a little problem that keeps me from being satisfied:
I need to access /dev/input/event1 to read from it, but the permissions mask for this node is 660 (rw-rw----). I can run `sudo chmod o+r /dev/input/event1` to make it readable for me, but this change is undone by the next reboot. I found that a change in /etc/udev/permissions.rules may help, but it doesn't. The line that handles event devices looks like this: [code]KERNEL=="event[0-9]*",  PROGRAM="/etc/udev/scripts/inputdev.sh %k", RESULT=="inputdev", MODE="0664", GROUP="keyboard"[/quote]But neither the MODE directive, nor the group change does anything, the file owner is still root.root and the permission mask is still 660. Also, the script inputdev.sh is only called for event2 (which is some speaker device), not for event0 and event1 (the two devices for my keyboard and mouse).

Is there a possibility in Ubuntu to make a device node permanently readable for other users or a certain group? The last way would be a init script that runs with su privileges and changes the permissions of the file, but this is not a very nice way, so I'd like to avoid this solution.

Thanks in advance
Thomas

---

