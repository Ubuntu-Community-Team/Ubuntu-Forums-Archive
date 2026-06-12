---
title: "Overheating Ubuntu 17.10 64bit"
date: 2018-04-23
forum: Hardware
---

### Post by luken2 on 2018-04-23
Hi everyone,

Few days ago I've installed Ubuntu 17.10 alongside with Win 10. Now It's getting heat when idle or locked screen. No heat at all when I boot from win10.
I had ubuntu gnome 16.04.4 64bit before. Never had overheating issue with it. Please help me to fix this problem. Otherwise recommend me a good distribution to install.

My laptop details:

Processor:	Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz
Memory:	8025MB
Machine Type:	Notebook
Operating System:	Ubuntu 17.10
Display
Resolution:	1366x768 pixels
Operating System Version
Kernel:	Linux 4.13.0-38-generic (x86_64)
C Library:	GNU C Library / (Ubuntu GLIBC 2.26-0ubuntu2.1) 2.26
Distribution:	Ubuntu 17.10

Processors:
Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz	3100.00 MHz
Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz	3100.00 MHz
Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz	3100.00 MHz
Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz	3100.00 MHz
Memory:
MemTotal	Total Memory	8025844 kB
SwapCached	Cached Swap	0 kB
SwapTotal	Virtual Memory	16776188 kB
SwapFree	Free Virtual Memory	16776188 kB


Thank you.

---

### Post by Autodave on 2018-04-23
You can always go back to 16.04. Or, you can wait for 3 days and 18.04 will be released (04-26).  16.04 and 18.04 are long term releases (LTS) which means that they will be updated and maintained for at least five years. All other release are only 6 months maintenance.

---

### Post by Yellow Pasque on 2018-04-23
> **Autodave said:**
> You can always go back to 16.04. Or, you can wait for 3 days and 18.04 will be released (04-26).  16.04 and 18.04 are long term releases (LTS) which means that they will be updated and maintained for at least five years. All other release are only 6 months maintenance.

Actually, they're 9 months, but I second the suggestion. Ubuntu 17.10 was their first attempt at using Wayland as opposed to Xserver, and it didn't go so well (they're switching back to X for 18.04). I've seen some performance complaints with 17.10 from intel users, so maybe try logging in with Xsession to see if there's a difference. But ultimately, you'll probably want to upgrade or fresh install 18.04.

---

### Post by luken2 on 2018-04-24
> **Autodave said:**
> You can always go back to 16.04. Or, you can wait for 3 days and 18.04 will be released (04-26).  16.04 and 18.04 are long term releases (LTS) which means that they will be updated and maintained for at least five years. All other release are only 6 months maintenance.

> **Temüjin said:**
> Actually, they're 9 months, but I second the suggestion. Ubuntu 17.10 was their first attempt at using Wayland as opposed to Xserver, and it didn't go so well (they're switching back to X for 18.04). I've seen some performance complaints with 17.10 from intel users, so maybe try logging in with Xsession to see if there's a difference. But ultimately, you'll probably want to upgrade or fresh install 18.04.

My poor experience force me to think 18.04 might be cause problems. I mean first month or two. I don't have much experience with new releases.
So you guys are recommending me to wait for 18.04 or go back to 16.04?

---

### Post by Yellow Pasque on 2018-04-24
Try this: [https://askubuntu.com/questions/961304/how-do-you-switch-from-wayland-back-to-xorg-in-ubuntu-17-10](https://askubuntu.com/questions/961304/how-do-you-switch-from-wayland-back-to-xorg-in-ubuntu-17-10)

> So you guys are recommending me to wait for 18.04 or go back to 16.04? 

17.10 is only supported for a few more months, so eventually you'll want to move to 18.04

---

### Post by sp40140 on 2018-04-24
What is the make and model of the laptop?
Also, there is a problem of big memory leak in gnome version of 17.10 ubuntu. Monitor your RAM usage over time and see what is happening there.
It makes sense to wait a bit and get 18.04.

---

