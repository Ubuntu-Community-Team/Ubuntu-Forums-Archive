---
title: "sony vaio touchpad"
date: 2010-11-26
forum: Hardware
---

### Post by hiraishin on 2010-11-26
so i bought a new sony vaio, PCG-71315L. i installed ubuntu using wubi the other day, because i need to program some stuff in c for class, but the touchpad doesn't work, as in it stays stuck in the middle whenever i try to use ubuntu. any suggestions?

---

### Post by falckon on 2010-12-31
I have the same laptop. I fixed the issue by adding i8042.nopnp to the kernel command line as suggested elsewhere. To be specific, open up a terminal and do the following:

[LIST=1]
[*]sudo nano -w /etc/default/grub
[*]Add i8042.nopnp to the GRUB_CMDLINE_LINUX_DEFAULT variable and save the file.
(i.e. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nopnp")
[*]sudo update-grub
[*]sudo reboot
[/LIST]

---

