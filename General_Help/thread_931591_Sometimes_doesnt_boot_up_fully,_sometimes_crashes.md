---
title: "Sometimes doesnt boot up fully, sometimes crashes"
date: 2008-09-27
forum: General Help
---

### Post by Beakster on 2008-09-27
Hi,

My installation was working fine for months, but seems to have developed an intermittent problem.

Sometimes the system freezes up, requiring a reset.  When this happens I cannot SSH to the box.

Sometimes when booting up it gets stuck, it seems to be always at a different point in the boot process.  When this happens it either freezes or occasionally loads up BusyBox.

At times it doesn't even get as far as Grub before it freezes.

I'm thinking possibly a hard drive fault.  I ran fsck without any parameters and the command line and it didn't appear to find any problems.

What else can I try?

Thanks
-Chris

---

### Post by Predator106 on 2008-09-27
Well you could try looking in the boot log files, hopefully it will be something consistent.

---

