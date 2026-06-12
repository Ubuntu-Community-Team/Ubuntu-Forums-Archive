---
title: "No throttling control or power management on second CPU core?"
date: 2009-06-30
forum: Hardware
---

### Post by ballejohn on 2009-06-30
Hi, as many others I have serious overheating issues since upgrading to Jaunty.

To stop the computer from shutting down all the time I've been forced to running my CPU at 800 Mhz all the time via the Gnome CPU Scaling Applet.. Anyway, I think I've found a clue:

john@john-laptop:/proc/acpi/processor/CPU0$ sudo cat info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes


john@john-laptop:/proc/acpi/processor/CPU1$ cat info
processor id:            1
acpi id:                 1
bus mastering control:   yes
power management:        no
throttling control:      no
limit interface:         no



My processor is an AMD TL-60, is it supposed to be this way? Shouldn't power management and throttling control be activated on the second core as well?

---

### Post by ballejohn on 2009-07-01
some more odd behavior:



if i've set the cpu scaling applet to ondemand, and the temperature of the CPU reaches 91c, it automatically clocks down to 800Mhz. but then it is a lot slower than if i've chosen myself to clock it down to 800Mhz with the applet.

and i think i know why.

i've checked the /proc/acpi/processor/CPU0/throttling and it is always set to T0, even when the CPU applet is at 800Mhz, unless it clocks down due to the temperature reaching 91c. then it goes down to T7 (12%).



maybe this whole laptop heat problem in jaunty is because of the T-states being wrongly controlled by the kernel?

---

