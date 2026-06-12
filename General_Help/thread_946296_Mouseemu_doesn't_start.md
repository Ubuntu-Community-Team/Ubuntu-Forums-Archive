---
title: "Mouseemu doesn't start"
date: 2008-10-13
forum: General Help
---

### Post by bcqdan on 2008-10-13
Hi,

When I start mouseemu, I get:

Trying to open /dev/uinput... error.
Trying to open /dev/input/uinput... ok.
ioctl UI_SET_KEYBIT: Invalid argument
mouseemu: Make sure uinput module is loaded or available in the kernel.

$ lsmod | grep uinput
uinput                 12544  0

I am stuck. Any ideas to debugging / fix this?

Thanks,
Bogdan

---

