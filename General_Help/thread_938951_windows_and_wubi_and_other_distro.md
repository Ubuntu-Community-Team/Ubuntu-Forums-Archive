---
title: "windows and wubi and other distro"
date: 2008-10-05
forum: General Help
---

### Post by Mine's Ultimate R on 2008-10-05
ok, so i have windows and wubi right now
i was wondering if i could then dual or triple boot opensuse or fedora (i dunno if wubi is considered dual boot)

how would this affect the bootloader if it was possible?

i like windows bootloader

thanks!

---

### Post by ago on 2008-10-06
You can install other distros, provided you keep the windows partition you will be able to boot into wubi. Note that the other distro will install in its own partition and replace the bootloader with grub wich will chainload the windows bootloader, there you will have the option to select windows or ubuntu.

---

### Post by Mine's Ultimate R on 2008-10-06
thanks for the reply!

but i'm not stupid, i know that wubi is installed inside windows so obviously if i removed windows then ubuntu would be gone

ahh darn, i would much rather have windows chain load grub, but whatever same difference

thanks for the helpssss!

---

