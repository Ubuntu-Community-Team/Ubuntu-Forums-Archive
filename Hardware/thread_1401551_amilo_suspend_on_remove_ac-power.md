---
title: "amilo: suspend on remove ac-power"
date: 2010-02-08
forum: Hardware
---

### Post by gagatz on 2010-02-08
hi,
i have the following situation: 
i have a fresh install of hardy on my amilo la1703 and if i pull out the ac-power cable it automatically thinks the battery is nearly empty (which it isn't) and goes to suspend within seconds. wake up is no problem, but i would like the computer to just ignore 'power-off' cause the cable sits quite loose and 'falls off' with every movement. i already told in the powermanagement to do nothing when battery is critically low. 
what can i do?
thanks, gagatz

---

### Post by gagatz on 2010-02-08
hi all, this issue solved itself. 
the trick was to pull the cable, and work on battery power until the battery is nearly empty. so gnome-power-manager was able to compute the battery charge. now gnome-power-manager does not assume anymore the battery is empty, although it isn't
greetings.

---

