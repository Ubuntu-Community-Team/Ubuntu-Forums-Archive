---
title: "Manually increasing fan speed"
date: 2011-11-03
forum: Hardware
---

### Post by Lars Noodén on 2011-11-03
Where are the controls for the system's fans in Oneiric?  How can I increase the fan speed manually?

---

### Post by ahiung on 2011-11-03
> **Lars Noodén said:**
> Where are the controls for the system's fans in Oneiric?  How can I increase the fan speed manually?

By replacing the dynamo? I guess that is the only way, because cool fan is already at their top speed.

---

### Post by Lars Noodén on 2011-11-03
I found it.

```

sudo echo 6200 > /sys/class/hwmon/hwmon0/device/fan1_output

```

But it can't go above /sys/class/hwmon/hwmon0/device/fan1_max

---

