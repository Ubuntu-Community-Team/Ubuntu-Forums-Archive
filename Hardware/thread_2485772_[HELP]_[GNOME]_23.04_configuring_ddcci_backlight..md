---
title: "[HELP] [GNOME] 23.04 configuring ddcci backlight."
date: 2023-04-09
forum: Hardware
---

### Post by lucio-a on 2023-04-09
I'm trying to run gnome backlight control on a external monitor using XF86 keys, autoloading ddcci modules but nothing shows at /sys/class/backlight.

lucio@biscoito:~$ lsmod | grep ddcci
ddcci_backlight        20480  0
ddcci                  49152  1 ddcci_backlight

Do I need any other special procedure?

---

