---
title: "psmouse errors startup and shutdown"
date: 2020-07-04
forum: Hardware
---

### Post by apg6xswhjc on 2020-07-04
I'm running 20.04 on a Dell 5587 laptop.

I receive errors on boot

```

[    1.956445] psmouse serio1: synaptics: Unable to query device: -5
[    7.896411] psmouse serio1: Failed to enable mouse on isa0060/serio1

```

Also, on shutdown, I receive an error something like 'Failed to disable mouse on isa0060/serio1', and it takes some time for it to fail before it does shutdown.

The touchpad works as expected, so I tried blacklisting psmouse in /etc/modprobe.d/blacklist.conf. But I still receive the errors, and lsmod shows the psmouse driver is still loaded :mad:

Any ideas on what I should do?

---

