---
title: "New(er) Linux Box"
date: 2016-11-01
forum: Hardware
---

### Post by guy42de26 on 2016-11-01
Thinking of upgrading to a newer (less old) platform for Ubuntu 16.4.  The two questions are:

1. Does Ubuntu support the Intel Xenon processors? and
2.  Will the Xenon multi-core processors make any noticeable difference from my old Intel 6300 dual core?

---

### Post by TheFu on 2016-11-01
Welcome to the forums.

Nobody supports Xenon processors. ;)  I suspect that is a typo.  Xeon processors are supported. 

"Intel 6300" is vague. There are a few different intel chips with that number.  Let's work on fishing for knowledge ... i.e. teaching you to fish.

The way I decide if any CPU upgrade is worthwhile is to compare general CPU performance numbers between what I have and what I want.  No benchmark is perfect, but some information is better than zero information.  So if we assume your cpu is an "Intel Core i3-6300", the approximate passmark for it is 5700.  Looking for any upgrade that I'd notice would mean a 1500 or greater passmark improvement would be needed.

When you look through some passmark lists, you'll see that specifying a line of CPUs ... like "xeon" will return some very low-end, some middle and some high-end performance numbers.  Also, there are different architectures over the years, so a xeon from 4 yrs ago won't be as capable as a new xeon.  The exact model matters greatly.  Also, with Intel CPUs, some lines don't have GPUs, so you'll need an addon graphics card.  I think xeon is like that - no GPU.

Also, don't forget that newer CPUs tend to use less power. Less watts usually means less heat, which means less cooling required, which means less noise created. That might be important.  I've been replacing 125W CPUs with 53W CPUs and have been replacing 35W CPUs with 17W ones around here.  My home office is much quieter and cooler.

[https://www.cpubenchmark.net/](https://www.cpubenchmark.net/) is a reasonable place to look at passmark data.  I always make a spreadsheet/table with CPU model, socket type, cost and passmark when I'm looking to build a new system.   pcpartpicker can make getting compatible parts easier, but I always check manually any final config before ordering.

If you have an "Intel Pentium E6300" - the passmark is about 1700. Not a bad desktop, but hardly speedy.
If you have an "Intel Core2 Duo E6300" - the passmark is about 1100 - definitely time for an upgrade.  Anything less than 1500 _feels_ slow to me.

Anyway - see my point about "6300" not being enough data?

---

### Post by mörgæs on 2016-11-02
You could also consider to keep the existing hardware, feeding it something lighter than Ubuntu. 

Have you considered X/Lubuntu or Mate?

---

