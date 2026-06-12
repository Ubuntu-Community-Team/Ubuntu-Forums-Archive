---
title: "Ubuntu 10.10 64Bit Wireless"
date: 2010-11-16
forum: Hardware
---

### Post by splosh5 on 2010-11-16
Hey, i recently duel booted Ubuntu 10.10 64Bit Onto a HDD that already had Windows XP. When i first ran Ubuntu It was running great and i downloaded my Nvidea Card Drivers & Latest Updates. And that is about all i had time for when i installed it. Anyway as i booted into it today, it was unable to find my Belkin Wireless G adaptor. Now it was working fine before and it has also been working for the last 3-5 Versions of Ubuntu. Also i checked to make sure that it was working on my Windows XP Partition and it works fine. (I am using Google Chrome to Write this.)It just does not show any Routers or anything like that. As i am running a PC i am unable to connect to a Ethernet port. If anyone has any Ideas that would be great.

---

### Post by TBABill on 2010-11-16
What chipset does your device use? Is it possible an update or a driver download blacklisted it or blocked it? You can try: ```
sudo rfkill list
``` to see if it is blocked. If it is soft or hard blocked you can ```
sudo rfkill unblock all
``` to remove it. Otherwise, post the output of ```
lspci
``` to get started and know what kind of device chipset you are working with.

---

