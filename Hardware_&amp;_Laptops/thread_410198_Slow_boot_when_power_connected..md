---
title: "Slow boot when power connected."
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by JSHN on 2007-04-15
Hi,

I have quite a strange problem that I cannot figure out.
I've been using Xubuntu for quite some time and trying to learn more
and more about it every day. And I'm browsing this forum every day and
really love you guys helping people out with all there problems!
I've been using Windows for a long time but now I'm trying linux and
I'm loving it more and more every day! :D

I've been tweaking linux very much and using only the necessary services and programs
to keep it as fast and light as possible.

Now to my problem.

When I boot my laptop with the power-cord connected, the bootup-time is: 46 seconds.
But when I'm booting on battery-power, the bootup-time is: 23 seconds?

I would have understood if the bootime was slower on battery but not the other way around??

Anyone knows what the problem can be??

I'm attaching the bootcharts if that helps.

---

### Post by JSHN on 2007-04-17
I solved this one on my own.
Added "noapic" and "nolapic" to the boot menu-lst.

Now I'm happy again! =)

---

