---
title: "Laptop Keyboard Only Works When Booted with USB Keyboard Plugged In"
date: 2011-05-15
forum: Hardware
---

### Post by nbadal on 2011-05-15
Hi, I recently wiped my old 10.10 installation to upgrade to 11.04. Everything worked fine on the old version, but after the new installation, the laptop's keyboard does absolutely nothing. No Caps Lock light, no virtual terminal access, nothing.

I did get it working once though by booting up with an external USB keyboard plugged in as well, and the keyboard still worked after unplugging the external once I was at the login screen.

What other info should I give to help find a solution to this?
Thanks in advance.:)

Laptop Info:
Lenovo Y560
Intel i7 Core
ATI Graphics card (not installed yet, just using stock drivers at the moment)
Old Install: Ubuntu 10.10 32-bit
New Install: Ubuntu 11.04 64-bit

---

### Post by nbadal on 2011-06-07
Bumping with updated info. I'm still having this problem, and booting into recovery used to fix it, and then it stopped.

I tried following the advice of a thread (that I found a week ago, I don't have the link) where it told me to add "locale=en_EN i8042.reset" to the grub boot options, which fixed the problem for a few boots, but now the keyboard stops working about 3 minutes into the computer session, no capslock lights, nothing. Also, the USB keyboard no longer fixes the problem.

I'd really like to use my computer without having to be in the Ubuntu LiveCD, so if anybody could help, I'd really appreciate it. :(

---

