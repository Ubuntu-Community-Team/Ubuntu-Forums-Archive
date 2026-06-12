---
title: "Kill certain processes when on battery power"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by makhand on 2006-07-12
I hate to start a new thread, but I havent been able to find an answer to this yet. I'd like to know what it would take to kill certain processes (automatically) when i'm running on battery power. For example, i run folding@home, but i would rather not have that run when i'm on battery power. Is there a good way not allow certain things to run when on battery power? Thanks all.

---

### Post by reacocard on 2006-07-12
idk if it's a "good" way, but /etc/acpi/power.sh is run every time you unplug/plugin your computer, so you could add some commands there. you could even add commands to restart those programs when you plug back in!

---

