---
title: "processor won't stop scaling"
date: 2008-05-24
forum: Hardware
---

### Post by gammyhand on 2008-05-24
I have uninstalled powernowd from my machine but my CPU is still scaling. Any ideas?

---

### Post by sdennie on 2008-05-24
If you really need to turn off CPU scaling, doing the following should work:

```

sudo sh -c "echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

```

You may have to do that for all cpu cores.

---

### Post by gammyhand on 2008-05-25
Thanks for that. Will give it a go.

Can anyone shed some light on why removing powernowd this time isn't working?

---

