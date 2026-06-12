---
title: "Extending battery life on laptop"
date: 2012-01-13
forum: Hardware
---

### Post by cliowa on 2012-01-13
Hey all,

I recently bought a Toshiba Portege R835 and set it up to dual boot with Ubuntu 11.10 and Windows 7. I have to say I am quite amazed at how well Ubuntu runs out of the box.

After having used it for a while now I notice how the laptop gets considerably hotter and runs louder in Ubuntu than in Windows. I browsed the web and read about all the different power saving ideas and tools (laptop-mode vs TLP, for example), but not being a very experienced user  - I don't actually know a lot about how the kernel and the modules etc work - I found it difficult to understand what reasonable things to do are. Below I list some of the info I think is relevant. Could any of you help me with setting up my laptop so it consumes less power? Thank you very much!

Powertop tells me:
My laptop has between 700 and 1200 wakeups per second, but the CPUs run mainly in high C modes (mostly in 7). A lot of the wakeups come from some firefox things, but also from hrtimer_wakeup and compiz.
Under Tunables it tells me that "VM writeback timeout" is bad. What is that, and how do I change it?
Similarly, I am told to "Enable SATA link power management for /dev/sda". What does that mean? Does that effect the performance of the drive?
Similarly, I should set up "Autosuspend for USB device Intel(R) Centrino(R) Wireless-N + WiMAX 6150 (Intel Corporation)". What will that do?

Thanks for your help!

---

