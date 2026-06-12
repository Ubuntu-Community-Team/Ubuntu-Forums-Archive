---
title: "How I can change the two processors frequency in a Core Duo?"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by Davigetto on 2007-01-12
Hello, I have an ASUS laptop, Intel Centrino Core Duo.

The two processors are CPU0 and CPU1. I want to put the two processors in powersave mode, but always only changes the status of CPU0, never CPU1. I can't change it with the aplett and with de comands:

sudo cpufreq-selector -c 1
sudo cpufreq-selector -g powersave

This should change CPU1 config, but changes the CPU0 config, not CPU1.

What can I do?

---

### Post by Davigetto on 2007-01-12
My problem is that I want to change the CPU1 to POWERSAVE mode (he is always in Userspace) and when I put it him Powersave, it only affects CPU0 all time,

---

