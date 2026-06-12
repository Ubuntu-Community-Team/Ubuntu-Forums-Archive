---
title: "ACPI - Dynamic CPU throttle"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by MeMo_oMeM on 2005-10-16
Hi! I am in deep trouble :( My Kubuntu slowed down extremely, and I figured out that the problem is the wrong behaviour of dynamic CPU throttling. It always goes down to 13% of the CPU speed (in other words, it is reduced by 87%), no matter what I try.

I tried to set it up manually using: 

   [FONT="Courier New"]echo 0 > /proc/acpi/processor/CPU0/throttling[/FONT]

and it worked... Well, just for a couple of seconds only!!!! :( It goes back to %13 soon.

Feeling desperate, I wrote a C code that updates the /proc/acpi/processor/CPU0/throttling every second in an infinite loop. But I have to run it as root, and I hate temporary solutions. 

I am nervous because I spent days to setup the linux in my dreams. I don't want to trash it all just because this stupid problem. Besides, I make a lot of performance tests and I must be sure that I always use 100% of the CPU.

PLEASE HELP!! :confused: 

Thanks in advance.

PS: I use Kubuntu Breezy, kernel 2.6.12-9-686 on a Sony Vaio PCG-K25 laptop.

---

### Post by AnkurKotwal on 2005-10-16
This is happening thanks to powernowd. In most cases, CPU scaling is a good thing :) But obviously you would prefer it not be there.

Run
```
/etc/init.d/powernowd stop
```

You'll want to change things such that powernowd does not start at bootup.

---

### Post by wilsonrm on 2006-01-13
Another alternative is to set the cpuscale yourself. 
(do as root or using sudo)

apt-get install cpufrequtils

cpufreq-set -g performance

alternatively you can set it to conservative or ondemand

enjoy

---

