---
title: "cant get windows mouse settings"
date: 2010-01-31
forum: Hardware
---

### Post by buckley310 on 2010-01-31
pretty much the only reason i dont have my laptop running ubuntu is the fact that i cant get the mouse settings the same as they are in windows. i always use the default mouse settings in windows and ive gotten very fast at it so when i work in ubuntu on my laptops touchpad i always end up missing buttons and stuff no matter what i set the mouse to. is there a way to get it the same as windows or find where the settings are saved so i can mess with the actual numbers without the limits?

---

### Post by IcarusR on 2010-01-31
synaptics is the driver. Checkout the manual.

```
man synaptics
```

Have to add settings to /etc/X11/xorg.conf

---

### Post by buckley310 on 2010-01-31
i got it. all u need to do is use the command 'synclient'

---

