---
title: "Battery not recognized, most probably not working"
date: 2019-09-08
forum: Hardware
---

### Post by zetomes on 2019-09-08
Greetings all!

Thanks to the **Ubuntu forums** I could made anew a friend's **Inspiron 1525** by installing it **Lubuntu **[COLOR=#000000]**18.04 LTS**. With the valuable help of some people I was able to restore the wireless recognition and speed the booting and shutting down.[/COLOR]

[COLOR=#000000]Now the next step is the battery. I think the battery was already not working or having charging problems before I formatted the computer. 
After I installed Lubuntu and also with the previous Microsoft installation, the battery icon was always the same indicating that there was zero charging.
I decided to take it during the changes made after (wireless problem and booting).
Now, when I insert it, the system doesn't recognize it during the booting.

I would like very much to know if the battery has any possibility of being recovered, or to close that matter and consider it dead.

Thanks in advance for your patience![/COLOR]

---

### Post by #&amp;thj^% on 2019-09-08
Can you include this also:
```
**upower -i /org/freedesktop/UPower/devices/battery_BAT0**
  native-path:          BAT0
  vendor:               LGC
  model:                45N1005
  serial:               736
  power supply:         yes
  updated:              Sun 08 Sep 2019 03:16:35 PM MDT (8 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              56.69 Wh
    energy-empty:        0 Wh
    energy-full:         56.9 Wh
    energy-full-design:  56.16 Wh
    energy-rate:         0 W
    voltage:             12.465 V
    percentage:          99%
    capacity:            100%
    technology:          lithium-ion
    icon-name:          'battery-full-charged-symbolic'

```

---

### Post by zetomes on 2019-09-08
Thanks for your attention!

for my surprise it was recognized this time, but the charging is always 0%.

here it goes: [**upower -i /org/freedesktop/UPower/devices/battery_BAT0**]("https://pastebin.ubuntu.com/p/3ZJM94Zr9N/")

---

### Post by #&amp;thj^% on 2019-09-08
Yes it warns of a low "percentage:          0%" so your aware.
But, I would first try cleaning the contacts on the Battery, and where the Battery connects to the Laptop.
See if that helps firstly.

---

### Post by zetomes on 2019-09-08
I'll do it,
many thanks!

---

### Post by CatKiller on 2019-09-08
That laptop is over 10 years old. If it's still got the original battery in, that is also over 10 years old. Over time batteries lose their ability to hold a charge; things like high temperatures, deep discharge, and fast charging cause them to degrade more quickly. That battery may simply be dead. You may still be able to get a compatible replacement, though.

---

### Post by #&amp;thj^% on 2019-09-08
Also worth a shot: [https://medium.com/@jcoterhals/wont-your-linux-laptop-charge-when-the-battery-s-drained-completely-this-may-fix-it-3dd7db3e8fd5](https://medium.com/@jcoterhals/wont-your-linux-laptop-charge-when-the-battery-s-drained-completely-this-may-fix-it-3dd7db3e8fd5)

---

### Post by zetomes on 2019-09-08
Many thanks for all your advices!
Cleaned all contacts, but nothing.
The BOOT setup doesn't have a FlexiCharger option.
I wonder if I update the BIOS that option would appear... but I don't know how to update the BIOS from a Linux system... #-o

---

### Post by CatKiller on 2019-09-08
> **zetomes said:**
> I wonder if I update the BIOS that option would appear... but I don't know how to update the BIOS from a Linux system... #-o

Generally the OS is irrelevant for BIOS updates: you stick the BIOS image on a FAT-formatted thumb drive and update it from the BIOS environment itself.

---

### Post by zetomes on 2019-09-08
Thanks, I will give a try!

---

