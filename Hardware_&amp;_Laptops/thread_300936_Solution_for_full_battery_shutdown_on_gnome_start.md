---
title: "Solution for full battery shutdown on gnome start"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by Nuak on 2006-11-16
Hi guys, I've managed to find a solution for the shutdown problem in some ACPI laptops with Ubuntu Edgy 6.10. With this issue, gnome shutdowns the laptop a few seconds after start when the computer runs on battery, even if the battery is in full charge.

Just execute this command in your terminal for each user that uses the machine:

```
gconftool-2 -s /apps/gnome-power-manager/use_time_for_policy --type bool false
```

---

### Post by LittleLebowski on 2006-11-18
Obvious bug, Edgy developers, what gives?  Many thanks for the fix.

---

### Post by Riggs on 2006-11-24
> **Nuak said:**
> Hi guys, I've managed to find a solution for the shutdown problem in some ACPI laptops with Ubuntu Edgy 6.10. With this issue, gnome shutdowns the laptop a few seconds after start when the computer runs on battery, even if the battery is in full charge.

Just execute this command in your terminal for each user that uses the machine:

```
gconftool-2 -s /apps/gnome-power-manager/use_time_for_policy --type bool false
```

Is this something we could add to sessions as well and have it work?

---

### Post by LittleLebowski on 2006-11-24
Just do it once and all will be well.

---

### Post by Riggs on 2006-11-24
That did it!  I can now use my Toshiba laptop without it shutting down right away.  Thanks for the help.

---

