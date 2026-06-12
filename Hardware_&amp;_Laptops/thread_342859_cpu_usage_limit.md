---
title: "cpu usage limit?"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by Mushroomi on 2007-01-20
Hi.

Is there a way to limit cpu usage, for example:
when i run a new game or something, CPU-usage goes up to 100%
can i somehow limit it to like 80% or something?

---

### Post by kidders on 2007-01-20
Hi there,

Unfortunately, the short answer to your question is no ... CPUs don't really work like that. The only way to force a computer to do something more slowly than it's able for is on power consumption grounds (ie by clocking down the CPU). Anything you tell your computer to do will always use as much of the CPU as possible. Don't forget that the idea that your computer can do more than one thing at the same time is an illusion.

What you *can* play around with though is CPU _time_, which is something your operating system has control of. The Linux kernel allocates processing time based on various criteria (eg process "priority"). In principle, processes with higher priority get the CPU for longer than those with a low one. Additionally, you can cap the CPU time available to individual users.

> can i somehow limit it to like 80% or somethingAs I mentioned, even if you could, you wouldn't actually be able to do anything with the remaining 20%.

Hope that helps.

---

