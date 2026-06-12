---
title: "Extending battery life"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by stryderjzw on 2005-10-29
Hi fellow linux users,

I'm using Breezy on a Averatec 5110P.  It seems to me that battery life is lower than on Windows, but I'm not trying to compare.  What are some ways of extending battery life?

Thanks!

---

### Post by mrmaple on 2005-10-31
Me too, I have the speed-step cpu throttling going, and everything else I can think of, but my battery only lasts an hour instead of usually lasting over two hours.  I just upgraded to Breezy, and it seems like the battery life is even less now.

I'm using a thinkpad T40 with the CPU throttled to 30% 600 MHz most of the time.

What else can I do to extend my battery life?  Thanks!

---

### Post by 23meg on 2005-10-31
Mine lasts as long as it does with Windows. Things you can do:

- Make sure laptop-mode is started by issuing the "sudo laptop-mode start" command
- Decrease display brightness
- Remove your battery when working with AC power for extended periods
- Bring your wireless killswitch to the "off" position when not using a wireless connection
- Kill unnecessary processes, turn off apps you're not using in order to save some cpu cycles
- Make sure nothing is causing cpu peaks, which may fool powernowd into thinking you have a high cpu load and throttle the cpu.

---

