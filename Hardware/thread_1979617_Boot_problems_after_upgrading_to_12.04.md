---
title: "Boot problems after upgrading to 12.04"
date: 2012-05-13
forum: Hardware
---

### Post by stefan2140 on 2012-05-13
I have an HP Pavilion dm6.
I upgraded from 11.10 to 12.04.

When I try to boot with the 3.2.0-24-generic kernel, I don't succeed. The system hangs after some seconds.

When I boot with the older 2.6.38-11-generic kernel, it works fine. 

What can be the problem here, and how do I solve it?
(OK the computer keeps working, but why the new kernel doesn't work and what can be the consequences of this?

Thanks,
Stefan

---

### Post by Utkarsh Ray on 2012-05-13
In the boot menu (accessible through F2 or something else)
enter recovery mode and select the option update grub
If you see your kernel name with appropriate images and files detected (lowest part of screen), the problem should be solved.

It is generally a practice in Ubuntu community to clean-install instead of upgrade. It doesn't (mostly) screw things up due to many packages already installed. Try the tutorial section of forum.

---

