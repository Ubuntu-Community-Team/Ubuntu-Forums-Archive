---
title: "T61 suspend hibernate idle timeout on battery"
date: 2008-08-10
forum: Hardware
---

### Post by fearlsgroove on 2008-08-10
Lenovo T61 with intel graphics won't suspend on idle timeout or hibernate on critical battery. The suspend timeout works fine when it's on A/C power. Manually suspending or hibernating also works fine usuaseemslly, however if the laptop has been suspended for along period of time, it incorrectly complains that it's failed to suspend.

I'd be happy to provide any additional info requested, but I dunno what's useful so that's all I've got to start.

Running amd64 hardy.

Thanks!

---

### Post by fearlsgroove on 2008-08-11
*bump* never post on a sunday..

---

### Post by sayad on 2008-08-11
some times having problem with agp gives problem with hibernating or stad by , i have experienced it in my pc.What so ever , in laptops there cannot be any problems liek that, if so - reinstall teh BIOS and get teh xp again.

---

### Post by fearlsgroove on 2008-08-11
thanks for the tip; unfortunately i still get the same result. I updated the BIOS just in case, however it's displaying the same symptoms.

Since it does suspend just fine when idle on AC power, or when suspended manually, I suspect this problem is actually in gnome-power-manager. I've looked at the g-p-m logs but I don't see any indications that it's fired any suspend script either when it works on AC power or when it doesn't work on battery.

Does anyone have any information on how I can set g-p-m into some sort of debug mode so I can gather more info? Any other suggestions?

Thanks!

---

