---
title: "Wrong Resolution"
date: 2010-01-04
forum: Hardware
---

### Post by Mannyrue on 2010-01-04
Ok im stuck on 800x600 and it won't let me change it or to detect my monitor..Im at a loss of what to do..

I am running ubuntu 9.10
So could anyone please help me out with this?..

Also im not good with scripts or anything so speak to me like you would a child haha..

Also if this is the wrong place to post this I am sorry.

---

### Post by Final Version on 2010-01-04
Go go ga ga? Nah ok, System>Administration>Hardware Drivers, it's self explanatory from there.

---

### Post by prshah on 2010-01-04
> **Mannyrue said:**
> im stuck on 800x600 and it won't let me change it or to detect my monitor.

Please give us more information on your hardware: Open a terminal (Applications-Accessories-Terminal) and post back the output from the following command```
lspci|grep -i -E vga\|graphics\|display
```

Please also include the make and model of your display (if you have it).

QuickTip: Check if "Ctrl Alt Numpad+" and "Ctrl Alt Numpad-" allow you to change your resolution. (+ = higher resolution, - = lower). At your own risk, please. If this doesn't work, it is likely that the correct driver is not installed/activated for your graphics card. The above information will help us in giving you specific steps for your graphics card.

---

