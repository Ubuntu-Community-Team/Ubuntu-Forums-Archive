---
title: "Battery information"
date: 2008-08-10
forum: Hardware
---

### Post by PauGNU on 2008-08-10
Hi

I would like to know using the console which is the battery life (time and % of charge). Is there a console command to know it?.

---

### Post by sergiom99 on 2008-08-10
I can do it in my laptop with:
```

cat /proc/acpi/battery/BAT0/info
cat /proc/acpi/battery/BAT0/state

```

good luck.

---

