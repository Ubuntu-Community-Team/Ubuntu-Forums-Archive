---
title: "Battery Problem"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by MiniZiper on 2007-05-28
So far. Ubuntu rocks!
Aside from the me being unable to enable DRI.

Well, I'm using a Compaq Presario 1720US

And Ubuntu doesn't like the battery apparently, because it always reports 0% o.o'
Its unplugged right now... and It shows 0% battery, but apparently it isnt 0% because I'm able to write this... :D

Anyhow, anybody know how to fix this?? Because I have to guess how long I have to plug it in without it shutting off on me.
Thanks!

---

### Post by snafu_az on 2007-05-29
I have a Compaq Presario 17XL570 and the battery always shows 0% . I don't know how different your model is.  Check to make sure acpi loaded. check to see if you have a /proc/acpi directory.

On my laptop I can run

watch cat /proc/acpi/battery/CMB0/state

it displays the battery status every 2 seconds.

present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            1440 mW
remaining capacity:      1906 mWh
present voltage:         14948 mV

I don't know why the battery status doesn't show correcty in the power manager.  Hopefully someone smarter than me knows why.

---

### Post by paul_and_ball on 2007-10-05
I have had the same issue. I have not tried the /proc/acpi directory yet. It would be nice if it were integrated in the desktop or panel.

---

### Post by mbc2000 on 2007-10-20
Has anyone solved this issue?  I have a Presario 1720US and switched to Kubuntu to get a working battery applet in the system tray by installing klaptopdaemon.

---

