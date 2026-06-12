---
title: "Laptop suspend"
date: 2005-02-01
forum: Hardware &amp; Laptops
---

### Post by paul.hendrick on 2005-02-01
Hi, 
having followed the instructions on getting my laptop so suspend/hibernate when the lid is closed, I still can't get it working. 
lid.sh and sleep.sh are both symlinked to /etc/acpi/actions/suspend.sh
I've also tried using hibernate, with hibernate support in the kernel.

If I run suspend.sh from a terminal, I just get this output:
```

 * Stopping hotplug subsystem...                                                    [ ok ]
Stopping laptop_mode.
Usage: /usr/sbin/laptop_mode {start|stop}
 * Starting hotplug subsystem...                                                      [ ok ]

```

and that's it. When I first ran it, I got an error about laptop-mode command not found, but I've linked laptop_mode to laptop-mode in /usr/sbin.

any ideas?

---

### Post by yexin218 on 2007-10-19
i couldn't suspend my laptop either.
and i should press power button to get it shutdown.
before upgrading,(7.04) suspend could work well.
I don't know why, something wrong with my system, or it is a bug....

---

