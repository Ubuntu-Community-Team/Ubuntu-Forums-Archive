---
title: "Taking too much processing power?"
date: 2009-09-01
forum: Hardware
---

### Post by GroogFish on 2009-09-01
I set a bunch of cool desktop effects and it runs smoothly but takes 20%-30% of my cpu processing power while resting. When I'm moving a window it takes 30%-40% of my cpu processing power. And while spinning the cube it takes 50%-65% of my cpu processing power.

Is this too hard on my computer? Maybe I should just live without the special affects?

---

### Post by tgeer43 on 2009-09-02
No, it's not like a car engine. CPUs are designed to be run at full capacity with adequate cooling.

Having said that, when I was running 9.04 32-bit with compiz on a 2.2GHz Dual Core my CPU usage averaged between 20-40% when sitting at the desktop. After switching to 9.04 64-bit it's a mere 1-4%.

tgeer

---

### Post by arcull on 2009-09-02
I give a vote for x64 too, see this [http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks]("http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks") However compositing has appetite for hw resources, so if you don't mind living without the cube, you can disable compositing, if I remember well it's shortcut is Ctrl+F12. Running top command from konsole may help you analyse which proceses are the most greedy.

---

### Post by GroogFish on 2009-09-02
> **tgeer43 said:**
> No, it's not like a car engine. CPUs are designed to be run at full capacity with adequate cooling.

Having said that, when I was running 9.04 32-bit with compiz on a 2.2GHz Dual Core my CPU usage averaged between 20-40% when sitting at the desktop. After switching to 9.04 64-bit it's a mere 1-4%.

tgeer

Do you need special hardware to use the 64-bit? I've always used 32 bit but I don't know what the difference is.

---

### Post by pjvandehaar on 2009-09-02
If it was made in the last 5 years, it probably does. Last 2, almost surely.  You can just try it -- put 64-bit Ubuntu on a USB stick.

---

### Post by briantoumbs on 2009-09-02
> **GroogFish said:**
> Do you need special hardware to use the 64-bit? I've always used 32 bit but I don't know what the difference is.


You need a 64 bit processor.

---

### Post by GroogFish on 2009-09-02
> **briantoumbs said:**
> You need a 64 bit processor.

How can I check for this?
If I get the 64bit version will it make my computer run all-around faster? Also does it mean it has twice as many colors as 32bit? Or is that completely unrelated? :P

---

### Post by tgeer43 on 2009-09-02
> How can I check for this?Type this in a terminal:
```
cat /proc/cpuinfo
```> If I get the 64bit version will it make my computer run all-around faster?No, not *all round* faster - it'll still be only as fast as it's weakest link (graphics card, memory, system bus, drives, etc.) but it *should be* noticeably faster and more responsive in many situations. Personally it made a *huge* difference on my machine.
Your mileage may vary.
> Also does it mean it has twice as many colors as 32bit? Or is that completely unrelated?Completely unrelated. That's a function of the graphics card.

tgeer

---

