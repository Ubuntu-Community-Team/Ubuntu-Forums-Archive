---
title: "fan issues with Karmic and Satellite L305-S5955"
date: 2009-11-04
forum: Hardware
---

### Post by Matthew T. on 2009-11-04
I used to be able to add 'acpi_osi="Linux"' to the boot parameters in menu.lst to make the cooling fan work but grub 2 has done away with that. I am able to add the line (minus the quotes, maybe I need escape characters)to the boot parameters in Karmic by editing /etc/defaults/grub and updating grub but the results are less than optimal. 

With only 3% CPU usage, my hard drive starts at 109 degrees F, goes up to 130 where the fan kicks in, gets cooled back down to 109, and the cycle repeats - all within the space of about 10 minutes. It seemed that the computer maintained a more consistent temp with Jaunty. Ideas?

---

### Post by Matthew T. on 2009-11-05
I've been running the patched kernel linked to at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337) for the last two hours and it seems to have solved my problem.

---

### Post by Matthew T. on 2009-11-09
Not solved after all. Arch Linux is really growing on me, though, and seems less buggy than Ubuntu.

---

