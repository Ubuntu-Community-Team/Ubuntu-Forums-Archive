---
title: "Computer stuck in an infinite hibernation loop"
date: 2012-03-20
forum: Hardware
---

### Post by fir3wir3d on 2012-03-20
Hello, I am running ubuntu 11.04 (2.6.38-13-generic, EMGD graphics driver). Frequently after my computer hibernates after the battery level falls below a certain level (this usually happens when suspend eats all my battery which on ubuntu seems to randomly take anywhere between 2h and a couple of days - but that's probably topic for another thread) it gets stuck in an infinite hibernation loop where resuming the computer will cause it to hibernate again due to misdetected battery level (0%) even when it is fully charged or connected to the power adapter. Currently the only solution I came up with is removing the battery completely, resuming ubuntu, suspending it, inserting the battery and waking it from sleep. Is there a way to fix the power management to detect proper battery level after hibernation? It should be noted that this only happens if the first hibernation was caused by low battery. Also is there a way to prevent 11.04 or 11.10 from hibernating after it has displayed the battery critically low message and was immediately connected to the power  adapter. This happens on all my laptops and is incredibly frustrating since gnome-power-manager will actually wait a long time between displaying the connect ac power warning and actually hibernating the computer and yet it doesn't seem bothered by the fact that the computer is already charging when it finally does.

---

### Post by gordintoronto on 2012-03-20
What is EMGD?

What is the exact brand and model of your laptop?

The obvious solution is to avoid hibernation, since it takes just as long to boot up as from power off. In the power settings, you may find a "shutdown" option rather than "hibernate" when power is critically low.

---

### Post by fir3wir3d on 2012-03-20
Well the problem with shutting down rather then hibernating is that when I suspend my computer and ubuntu decides to randomly drain my battery from full charge within a few hours of sleep as it likes to do quite often I will loose all my unsaved work, open windows, browser tabs, etc. The whole idea of hibernation is to preserve work while the computer is not powered. A better solution would be some way to fix the incorrect battery level reading after the computer wakes up.

EMGD stands for Intel's Embedded Media and Graphics Driver and it's the current, ubuntu recommended driver for GMA 500 cards (see here: [https://launchpad.net/~gma500/+archive/emgd-1.8](https://launchpad.net/~gma500/+archive/emgd-1.8)). My laptop is ASUS 1201ha.

---

