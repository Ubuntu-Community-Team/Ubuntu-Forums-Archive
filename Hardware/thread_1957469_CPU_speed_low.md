---
title: "CPU speed low"
date: 2012-04-12
forum: Hardware
---

### Post by Tasteless on 2012-04-12
Hello everyone!

I've a dedicated server running with Ubuntu 10.04, Intel i5 2.80Ghz, 16GB RAM et cetera.

I used /cat /proc/cpuinfo to see how the CPU performed but it showed less speed then it should...

All 4 cores got 1600 MHz in speed but it should be nearly 2800 MHz.. I've done some hardware tests and it didn't show any errors. Could there be something with the Ubuntu version?

```

model name      : Intel(R) Core(TM) i5-2300 CPU @ 2.80GHz
stepping        : 7
cpu MHz         : 1600.000
cache size      : 6144 KB

```I apperciate all answers!

Thanks in advance.

---

### Post by newbie-user on 2012-04-12
All the mobile processors that I've used can underclock when running idle or low use. Maybe this is happening with your processor?

---

### Post by Tasteless on 2012-04-12
It could be perhaps not sure though. Do you have any good suggestion to see the performance of the CPU? Could be that cpuinfo isn't showing correctly either.

---

### Post by newbie-user on 2012-04-14
Are you running the server with a gui? If you are, there's an applet for gnome-panel that lets you control the cpu speed. I'd have to search around to see if there are any utilities to do the same on a CLI only system.

---

### Post by Yellow Pasque on 2012-04-15
It's supposed to run at lower speed when idle. Don't mess with it (unless you're one of those people that insists on wasting power by running the CPU at full speed/voltage when it's doing nothing).
> I'd have to search around to see if there are any utilities to do the same on a CLI only system.
cpufrequtils package..

---

