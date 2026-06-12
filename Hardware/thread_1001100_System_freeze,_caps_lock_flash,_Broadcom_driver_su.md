---
title: "System freeze, caps lock flash, Broadcom driver suspected"
date: 2008-12-03
forum: Hardware
---

### Post by danzvash on 2008-12-03
Problem: the system freezes hard, with caps lock flashing, and cannot be recovered, making a power cycle necessary.
This happens randomly, sometimes minutes after boot-up, sometimes after many hours.

System: HP tx2500z Tablet using x86_64 Ubuntu Intrepid 8.10, all packages up to date as of Dec 8 2008
(active repos: intrepid/-updates/-security main restricted universe multiverse)

This problem ONLY occurs when the wireless switch is enabled (I have confirmed this with weeks of testing)

Kernel ver:  2.6.27-9-generic
Broadcom driver version: linux-restricted-modules-2.6.27-9-generic 2.6.27-9.13
(broadcom driver "wl" is in restricted modules package)
Relevant hardware: Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

The exact same behaviour occurs with the previous kernel version (2.6.27-7-generic and corresponding restricted module package)

I *believe * that this problem has only happened when wireless signal strength is low (<40%).

dmesg, lspci -vvnn, and /proc/interrupts included in attached file.

Bug reported: [https://bugs.launchpad.net/bugs/304926](https://bugs.launchpad.net/bugs/304926)

---

### Post by sergiom99 on 2008-12-03
check this thread: [http://ubuntuforums.org/showthread.php?t=976287](http://ubuntuforums.org/showthread.php?t=976287)

---

### Post by danzvash on 2008-12-05
@sergiom99:
Yes, it appears that the thread you reference reports the same issue.
However, the users in that thread are reporting kernel panics / freezes with caps lock flash using a **variety** of wireless cards, including Intel and Atheros chipsets as well as Broadcom.

There is also no solution provided in the thread, though it seems a possible workaround may be to use Ndiswrapper with Windows drivers. I am loath to go that route though, I have to say.

I would love to hear some word from the Ubuntu team that this is an acknowledged issue. 
My bug report at [https://bugs.launchpad.net/bugs/304926](https://bugs.launchpad.net/bugs/304926) hasn't received any response yet.

---

### Post by tgraupmann on 2011-08-02
I have been experiencing the same issue.

IBUYPOWER D9T.

With a broadcom wireless card. Low signal strength.

I've since been using an external RangeMax 121T wireless adapter.

To avoid the issue I'd like to disable detection of the broadcom device entirely.

I can boot when the machine is cold one time. After that all reboots lock up.

Ubuntu 11.04 32-bit.

---

### Post by tgraupmann on 2011-08-02
This looks like a good solution:
[http://bigbrovar.aoizora.org/index.php/2011/04/30/turning-wireless-on-causes-laptop-to-freeze-on-ubuntu-11-04-natty-narwhal-my-work-around/](http://bigbrovar.aoizora.org/index.php/2011/04/30/turning-wireless-on-causes-laptop-to-freeze-on-ubuntu-11-04-natty-narwhal-my-work-around/)

---

