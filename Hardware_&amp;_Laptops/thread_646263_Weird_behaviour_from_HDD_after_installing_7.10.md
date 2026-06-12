---
title: "Weird behaviour from HDD after installing 7.10"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by Milambar on 2007-12-21
I recently put Ubuntu 7.10 on my laptop (which is really just a desktop replacement, as I never take it anywhere). After which, I noticed a noisy hard disk. Fearing the worst (the drive is old), I installed smartmontools, and noticed a very high load cycle count.

To double check, I ran smartctl again, and what? The load cycle count had gone up by 5 in the space of 1 minute. I made a simple script, to check the load cycle count every 30 seconds, logging the output to a textfile, and let it run for an hour.

The result is, Ubuntu seems to be parking and unloading the heads, 5 times a minute. Erm, that can't be right... Or good for such an old drive... Especially one thats permanently connected to the mains, so doesn't even need to conserve power..

A bit of searching around, and I found hdparm -B254 /dev/sda, and that stopped it.

However, I'd like to make that a permanent change, so it lasts even through  a reboot. How do I do that?

---

### Post by anubhavrocks on 2007-12-21
Put the command in /etc/rc.local

---

