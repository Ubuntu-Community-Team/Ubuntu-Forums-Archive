---
title: "Battery Life on HP 6930p"
date: 2010-01-06
forum: Hardware
---

### Post by Daug on 2010-01-06
Hello--
I've installed Karmic on an HP 6930p, and everything works, but battery life is very poor.  At 100%, it says there is 2hr30min remaining, but then 35min later, it reads 1hr35min remaining. So, ultimately, I think I'm only getting about 1.5hrs on a full charge.  This is worse even than my installation of Hardy on an OLD Toshi Satellite M20. Especially when I boot into XP Pro, and get 4.5hrs on a full charge...  Does anyone know of a package of HP drivers or something that could help?  I really don't want to go back to XP, but I may have no choice =(  Any help is greatly appreciated, as are installation instructions.

Thanks!

---

### Post by shilo on 2010-01-07
You can try enabling laptop mode to see if it helps.

First:

```
sudo gedit /etc/default/acpi-support
```Change ```
ENABLE_LAPTOP_MODE=false
``` to ```
ENABLE_LAPTOP_MODE=true
```Reboot the system and see if that helped.

You can check to see if laptop mode is enabled by:[FONT=monospace]

[/FONT]```
[FONT=monospace]cat /proc/sys/vm/laptop_mode[/FONT]
```

---

