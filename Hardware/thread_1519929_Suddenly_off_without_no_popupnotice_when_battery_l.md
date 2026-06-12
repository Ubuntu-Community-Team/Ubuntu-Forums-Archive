---
title: "Suddenly off without no popup/notice when battery low"
date: 2010-06-28
forum: Hardware
---

### Post by xjukie on 2010-06-28
Im using Ubuntu on my Macbook Pro, whats annoying me is, when im using AC (Battery) Ubuntu will not notice me or appear any popup when the battery left let say 2mins more. (im practising using battery until around 5-10% like that.
So the machine will suddenly off (without proper poweroff).

The battery indicator sometimes didnt show the power left.

---

### Post by nixscripter on 2010-06-29
See what the system thinks about the battery:

```
cat /proc/acpi/battery/BAT0/info
```

BAT0 might be named something else.

In particular, look at the capacity. That's how HAL/ACPI make decisions about when to hibernate/switch off the computer.

---

