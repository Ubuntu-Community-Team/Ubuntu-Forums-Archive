---
title: "Acer Aspire 1524WLMI Overheating"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by Rincewind on 2006-08-06
Hi,

Seems to be since the last few kernel updates, I'm getting auto shutdown when doing anything CPU intensive due to overheating.

I think this may have something to do with it(!):

```
cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no
```

```
cat /proc/acpi/processor/CPU0/throttling
<not supported>
```

Frequency scaling seems to be working as it should - idles at 800Mhz and steps up to max 2.2Ghz.
Any ideas?  I'm having a go at compiling a custom DSDT i found to see if this helps.

Rincewind.

---

