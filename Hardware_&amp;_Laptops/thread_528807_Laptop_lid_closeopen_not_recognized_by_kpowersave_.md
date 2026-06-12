---
title: "Laptop lid close/open not recognized by kpowersave after unplugging"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by strabes on 2007-08-18
Title says it all. See the following:```
alex@alex:~$ lshal --monitor

Start monitoring devicelist:
-------------------------------------------------
09:22:38.693: computer_logicaldev_input_2 property button.state.value = true
09:22:38.695: computer_logicaldev_input_2 condition ButtonPressed = lid
09:22:39.907: computer_logicaldev_input_2 property button.state.value = false
09:22:39.909: computer_logicaldev_input_2 condition ButtonPressed = lid
```

So, the lid close event is being recognized by HAL, it's just that kpowersave isn't doing anything about it.

---

