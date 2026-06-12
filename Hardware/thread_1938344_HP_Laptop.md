---
title: "HP Laptop"
date: 2012-03-09
forum: Hardware
---

### Post by fred0843 on 2012-03-09
Hp G72 laptop will drain battery.This does not happen if I turn it off with windows.

---

### Post by Jon Monreal on 2012-03-09
Hello,

Could you be a bit more specific, such as stating if it's the wireless that's draining the battery? Thanks.

---

### Post by fred0843 on 2012-03-09
Laptop is Wireless
I use the menu to shutdown the laptop

I do not know of any other way to shutdown.Other then force shutdown with the power switch

---

### Post by Jon Monreal on 2012-03-09
> I use the menu to shutdown the laptop

I'm still not entirely sure what the actual problem is.

Is it a power drain issue, or an issue with shutting the computer down?

If the problem is just turning off the wireless without using a physical switch, you should be able to uncheck "Enable Wireless" in the network manager.

---

### Post by Basher101 on 2012-03-09
my guess is that even when he clicks shutdown it keeps running somehow and drains the battery. If the menu shutdown does not help, try it with a command in the terminal```
sudo shutdown -h now
``` to immediateley shut it down

---

### Post by fred0843 on 2012-03-09
I turn off the Laptop.
Battery Charged 100%
If I leave it off for a few Days.The battery will show charge at 87 %

For the same time if shutdown with windows the battery is still at 100 % charge.

---

### Post by Jon Monreal on 2012-03-09
If the battery is charged, and you first start up the laptop, it should have roughly the same charge in Windows in Ubuntu.

The difference here is that Ubuntu is likely saying 87% for some reason because it's likely only charged to 87% of the design energy full, as where Windows is saying 100% because it's charged to 100% of that 87% to which it still charges.

Over time, the battery can charge to less and less its original design charge. It would seem that for some reason, then, Ubuntu hasn't updated its number for energy when full.

This is no cause for alarm, and is a difference only in terminology, and has no bearing on reality (Ubuntu's 87% = Windows' 100%).

---

