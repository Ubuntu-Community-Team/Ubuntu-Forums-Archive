---
title: "Laptop Wont Powerdown"
date: 2008-11-01
forum: Hardware
---

### Post by lch503 on 2008-11-01
I am running ubuntu 8.10. When I shutdown i get to the shutdown screen the bar completely turns black, then the hard disk shutdown then the cpu fan and the screen stays on. Then it hangs. I have seen what the laptop is doing behind the splash screen. There are no errors and Power Down. appears but the laptop stops here. I have to hold the power button to turn the laptop off Have tried numerous things including.
At boot time
acpi=force
acpi=force lapic
power_off
lapic

And also adding
-to etc/modules
apm poweroff=1

Nothing seems to work and I dont like holding the power button down to turn off the laptop. If you need anymore details please ask and provide the code necessary to do it as I am fairly new to ubuntu. Please Help!

---

### Post by anthonie on 2009-01-01
Same problem here. Running 8.10 on a new asus laptop X50GL. I switched off quiet splash to see what's happening. I get down to tty1, than powerdown simply hangs and I have to press the powerbutton to really switch off the laptop.

Suggestions anyone?

---

### Post by anthonie on 2009-01-26
Bump!

Still looking for a solution to this powerdown problem. Also, the ubuntu image (from quiet-splash) is corrupted when switching off the computer. Upto the very last stage of powering down everything works really fast and smooth, untill it halts and I have to press the powerbutton a couple of seconds to really turn the machine off. No probs with rebooting though...

---

