---
title: "abnormally high CPU usage on Kubuntu 64 bit"
date: 2012-02-03
forum: Hardware
---

### Post by boddhisatva on 2012-02-03
Hi
I've got a fresh Kubuntu installation with just a few tweaks added (e.g. Cairo-Dock) and when I've turned on a CPU monitor for my AMD quad-core it seems all the cores are being used at 25%, accordning to CPU usage applets, even with no active apps. There are no applications showing in the System Monitor which use that processing power. The default System Monitor shows all the cores are being used, with variation, around the avarage of 25%. Any ideas?

---

### Post by sudodus on 2012-02-03
What is it doing? Check what processes have the highest cpu load? What I notice, is that while you are displaying the graphical output of the system monitor, your computer will be more busy than while you are showing a list. Try ***htop*** if you want a system monitor with a small foot-print, yet much better than good old top.
```
sudo apt-get install htop
```

---

### Post by boddhisatva on 2012-02-03
In htop it looks like plasma-desktop and especially kwin are using the most - 10 to 30% CPU power (or more) on average. I've also tried Mint KDE RC from a live CD, just to see how it compares, and the footprint is A LOT smaller, so I don't think it's normal.
I should add that the settings for kwin (desktop effects) are the default ones.
Another process that seems to eat up a lot of CPU power is virtuoso.

---

### Post by sudodus on 2012-02-03
OK, the test with Mint shows that something is not running well in Kubuntu, and since the desktop is using a lot of the cpu, I suspect that inefficient graphics might be the problem. What graphics card or chip is it? Have you enabled a proprietary driver? Maybe you can check what driver is used by Mint.

---

### Post by boddhisatva on 2012-02-03
Thanks for the suggestion. I've enabled a driver update (a post-release version) and it seems to have done the trick. Now it's looking a lot more decent! :D
Thanks again!

---

### Post by sudodus on 2012-02-03
You are welcome :-)
Please mark this thread SOLVED

---

