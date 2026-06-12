---
title: "Atheros wireless card (AR5008) randomly not being recognized with ath9k"
date: 2011-06-06
forum: Hardware
---

### Post by danakim on 2011-06-06
Hi all,

I have been running Ubuntu 10.10 on my HTPC for a while now without any issues. But wanting to make things as cable free as possible I have bought a TP-Link TL-WN951N wireless card - based on the AR5008 chipset. The problem with this card is that it is intermittently recognized at boot time.

Approximatively 2 out of 3 boots fail to see any wireless interfaces. Every time this happens, "lsmod" reports ath9k as being loaded and used, "lspci" list my wireless card correctly - but all of the user space utilities fail to "see" or use the card: ifconfig / iwlist / iwconfig / network manager etc. 

Subsequent reboots will fix this issue "magically". 

There is absolutely nothing useful in the logs - no errors, nothing - because the system does load the driver but somehow doesn't manage to use it. 

I have tried stopping irqbalance - thought it was an irq mess up somewhere. Upgraded the kernel, tried to the latest ath9k from source, tried to pass the option of "no hardware encryption" to the module (the only option available) - nothing solved the problem.

Have any of you encountered a similar problem? Any ideas on what else to try or what to do to get more verbose debugging of the problem?

Thanks!

---

### Post by Yellow Pasque on 2011-06-06
There should be something in dmesg on a failed boot indicating no interface available. If not, this thing's going to be hard to troubleshoot, especially if it's not fixed upstream.

Good luck. Wireless can be a pain. I have a Netgear WNA1100 and it works out of the box with modern distros.

---

### Post by danakim on 2011-06-06
Thanks for the advice Temüjin! Unfortunately dmesg doesn't show anything.. :( tried that. 

Yeah, unfortunately wireless is still a pain in Linux!

I might give mad-wifi a go too, see if things are looking better, if now I will switch to a usb wireless card I have lying around - although I was trying to avoid that because it means switching back to wireless g instead of n.

---

