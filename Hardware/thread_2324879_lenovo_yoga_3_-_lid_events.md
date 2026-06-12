---
title: "lenovo yoga 3 - lid events"
date: 2016-05-17
forum: Hardware
---

### Post by no_name4 on 2016-05-17
hi all

I got a new Lenovo Yoga 3 (11"), and I'm trying to configure it to work with all the lid positions.
There is no automatic configuration, with one exception: when I completely open the lid (360 degrees=tablet mode), the keyboard is disabled.
I'm trying to understand which program or module controls that, but I couldn't. There's a dmesg comment:
```
 ideapad_laptop: Unknown event: 10
```
but I don't think it's the only cause for controlling keyboard.
I tried to look for acpi events, but couldn't find one that looks relevant.

When I understand that, I can continue with my research and hopefully write a complete script, to handle all positions.

Thanks

---

### Post by no_name4 on 2016-05-19
Up

Any idea where to start looking?

---

