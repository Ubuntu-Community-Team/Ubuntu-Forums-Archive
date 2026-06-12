---
title: "laptop hard drive spins up/down/up/down"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by acranox on 2007-02-03
I've got a Dell D600, I'm running Edgy.  I don't run on battery too often, but I'm running on battery now and my hard drive keeps spinning down after just a couple seconds of idle, and then of course as soon as I do anything it spins back up.  It is cycling several times a minute.  This is ridiculous.  I'd like it to stay spun up, and only go idle after 2 or more minutes of inactivity.  I've got laptop_mode enabled, and I tried changing LM_BATT_HD_IDLE_TIMEOUT_SECONDS in the laptop.conf file, but nothing seems to be having any effect.  What is going on?
Now when I check "cat /proc/sys/vm/laptop_mode"   I'm getting 0, so I guess the machine isn't even going into laptop_mode.  But I'm pretty sure that earlier I was getting a value of 2.

Help?
--Peter

---

