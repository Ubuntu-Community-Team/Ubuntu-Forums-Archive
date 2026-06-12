---
title: "Lock Screen"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by gaberade on 2006-04-27
How would I go about disabling the lock screen function when I shut the lid on my laptop?

It's a Dell Inspiron 9100.

---

### Post by jackmc on 2007-04-26
me too (different laptop, I assume same instructions :))

---

### Post by jackmc on 2007-04-26
This worked for me: 

> **23meg said:**
> ```
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false
```should do it.

---

