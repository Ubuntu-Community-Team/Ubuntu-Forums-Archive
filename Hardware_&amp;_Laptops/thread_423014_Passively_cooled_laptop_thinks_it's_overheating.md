---
title: "Passively cooled laptop thinks it's overheating"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by N3d on 2007-04-25
I have an Acer Travelmate C113. It's a very small laptop with no CPU fan, just some copper heatpipes. The preinstalled Windows XP Tablet Edition evidently does something funky with frequency scaling, because it never goes over 54 degrees C.

Other than that, it's a very normal Centrino, 1.2 GHz Pentium M.

Feisty installs and runs okay to begin with, but under load the CPU warms up, as you might expect. The Pentium M is officially okay to 100 degrees. But the problem is, when the CPU reaches 66 degrees, it suddenly appears to jump to 95 degrees.  Throttling kicks in, going by /proc/acpi/processor/CPU0/throttling. It increases one throttling stage every minute or so, and the temperature never appears to drop (although it almost certainly must be cooling down in reality).

Eventually it reaches T7 and the machine is unusable. It can't even shut itself down.

Interestingly, when running on the Live CD, it is actually capable of returning to "normal" temperatures and removing the throttling.

Unfortunately this means I'm constantly working with one eye on gnome-sensors-applet so I can shut everything if the temperature gets too high.

In summary: can anyone think of any reason the temperature would jump from 65 to 95, and then not come down?

Thanks in advance.

---

### Post by ksosez on 2007-04-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/22336](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/22336) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Check out this bug. I am seeing it with my Thinkpad. Looks like its known

---

