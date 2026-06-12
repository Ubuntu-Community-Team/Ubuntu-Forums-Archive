---
title: "laptop-mode tunable"
date: 2012-06-15
forum: Hardware
---

### Post by piriton on 2012-06-15
I would like to setup laptop-mode-tools so that I can benefit from longer battery life under Linux.

I Installed the laptop-mode-tools package under the impression that this would enable the kernel tunable laptop_mode, however when I examine the kernel value, it's not set.

What am I missing ?

```

$ cat /proc/sys/vm/laptop_mode 
0

$ dpkg laptop-mode-tools
ii  laptop-mode-tools               1.60-1ubuntu1                   Tools for Power Savings based on battery/AC status

$ grep ENABLE_LAPTOP /etc/laptop-mode/laptop-mode.conf 
ENABLE_LAPTOP_MODE_TOOLS=1
ENABLE_LAPTOP_MODE_ON_BATTERY=1
ENABLE_LAPTOP_MODE_ON_AC=0
ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=0

```

---

### Post by Redblade20XX on 2012-06-15
Maybe this will help: [https://wiki.archlinux.org/index.php/Laptop_Mode_Tools](https://wiki.archlinux.org/index.php/Laptop_Mode_Tools)

- Red

---

