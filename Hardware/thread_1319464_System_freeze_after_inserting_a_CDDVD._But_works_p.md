---
title: "System freeze after inserting a CD/DVD. But works properly in the root console"
date: 2009-11-08
forum: Hardware
---

### Post by gemme on 2009-11-08
Hello

I am not able to use my LG GSA-4167B drive (IDE, no SATA) under Gnome. When I insert it, it doesn't get mounted. The disc in the drive is working for a while (I can hear it's spinning), then it stops and the system hangs completely (no input from the keyboard or mouse works, even the magic Alt+SysRq+... keys).

All the logs are empty (there are no errors, before and after the freeze, including system boot) - I've checked even the Xorg's ones. The lshal --monitor gives nothing, sudo udevadm monitor -e too.

Strangely, the drive works perfectly when I select "recovery mode" in Grub and go to the root shell. I am able to mount /dev/scd0 and browse it. So it's not a kernel bug (in Windows it works ok too).

How can I make it work (I am not able to burn a backup or open my documents in text console)?

Or at least produce some debug info?

Any way? Please? :(

---

