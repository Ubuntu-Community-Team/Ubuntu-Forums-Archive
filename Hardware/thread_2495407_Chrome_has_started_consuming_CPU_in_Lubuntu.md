---
title: "Chrome has started consuming CPU in Lubuntu"
date: 2024-02-17
forum: Hardware
---

### Post by mcman56 on 2024-02-17
I have been running Lubuntu on one computer for a few years.  Performance has really degraded over the last few months and when I run the qps monitor, I see chrome consuming most of the CPU.  When idle the usage does go down.  See attached screen print.  I ran memtest 86 plus and it passed.  How can I diagnose?  Could updates to Chrome and Lubuntu require more computer power so this system is getting obsolete?  Falkon does run better but it less desirable.

Lubuntu Ubuntu 22.04.4 LTS
Gateway NE71B
AMD Dual-Core Processor, 1400 MHz
8 GB Memory


Google Chrome
Version 121.0.6167.184 (Official Build) (64-bit)
[IMG]https://ibb.co/cJr4KQH[/IMG]


[IMG]https://ibb.co/3NvXD4t[/IMG]

---

### Post by guiverc on 2024-02-17
I don't use chrome, so can't really advise there (I do use chromium, but given its a *snap* package it maybe somewhat different).

Have you made any change(s) to chrome, esp. addons..  Are your addons leaking RAM??  as I've had issues before with addons for chromium/firefox that after a number of hours leaked RAM which slowly filled swap & then started causing issues.. The issue only occurred with those extensions installed; so I had a choice of either stop using them, OR manage the issue.. I opted to manage the issue (*detecting when leaking reached a point, then just close browser(s), let system unclear used RAM, then restart browser(s)*) as I liked what the extensions provided me.

Have you increased swap to something appropriate?; Lubuntu's use of `calamares` means very little swap is used by default; too small for most of my older/resource-limited hardware, thus increasing swap is essential for me (*to maintain performance*).

Maybe useful
- swap FAQ [https://discourse.lubuntu.me/t/swap-and-lubuntu-faq/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-faq/2591)
- creating swap files [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

You can use `free -h` to view RAM quickly; and see the swap line too

---

### Post by mcman56 on 2024-02-17
I checked memory while the cpu was highly utilized but I think it shows memory as OK  See attachment.

It does seem odd to me that it is not using any Swap.  I also wonder the "Priorit -2" means.

---

