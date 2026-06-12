---
title: "mousepad of Asus Eee PC 1005HA on 11.04 (Gnome)"
date: 2011-08-18
forum: Hardware
---

### Post by Hellbourne on 2011-08-18
Hi,

I have an Asus Eee PC 1005HA running Ubuntu 11.04 with Gnome 2. I upgraded to 11.04 back in May and up until now everything was fine. 

Then, all of a sudden, as far as I remember, the mousepad stopped working. This is not a hardware problem, since the mousepad *does* work on the login screen. It stops working, though, once I log in.

Has anyone encountered a similar problem? Do you know what is going on? I am kind of lost here.

Thank you,

Amit

---

### Post by Hellbourne on 2011-08-18
so apparently 
```

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true 

```
works but the question is what changed? what happened? Is the above command permanent?

Amit

---

