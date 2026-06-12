---
title: "Lidbtn ACPI event never triggered, backlight doesn't turn off"
date: 2009-06-30
forum: Hardware
---

### Post by speaker219 on 2009-06-30
I'm having a problem with my laptop lid in Ubuntu 9.04. The lidbtn event is never triggered when the lid is closed. /proc/acpi/button/lid/LID0/state reports the proper states (open or closed), but the lid.sh script is never executed.

My laptop is a Dell Studio 1555.

I can confirm this because my backlight does not turn off when I close my lid, but if I have this running:
```
while [ 1 ]; do /etc/acpi/lid.sh; sleep 1; done
```
The backlight turns off when the lid is closed, and back on when I open it. Any ideas? making me crazy :[

---

### Post by rengolin on 2009-10-22
Same problem here... Dell studio 1555.

Can you make your laptop to suspend? Did you install kernel 64-bit?

---

