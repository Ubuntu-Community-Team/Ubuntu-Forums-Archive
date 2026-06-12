---
title: "Ethernet/Wireless/Battery gone??!!!"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by wreckingcru on 2005-04-13
I just installed Hoary 5.04 on my Gateway M210 Laptop with a dual boot (WIN XP).

The first time I ran it after the install - it was smoother than James bond. It picked up wireless seamlessly. When i plugged in ethernet, All i had to do was load the tray icon and activate it and it was up and running.

I restarted my computer for something - and NOTHING WORKS NOW!! It doesn't detect either ethernet (eth0) or wireless (eth1) and my battery indicator on the status bar (which would properly show plugged in) now shows no battery left and refuses to change to anything else.

I've been surfing this forum trying ifup -a , iwconfig, checked the interfaces file....everything looks ok...
Since I can't get that damn computer to get on the net - it's hard to post the results of these, but to summarize - nothing has let me activate the wireless or the ethernet (it just says the device does not exist) ...

I know they work - since I checked them loading XP and they were both running fine.

Any suggestions? Is the only solution a re-install?

Thanks

PK

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=wreckingcru]I just installed Hoary 5.04 on my Gateway M210 Laptop with a dual boot (WIN XP).

The first time I ran it after the install - it was smoother than James bond. It picked up wireless seamlessly. When i plugged in ethernet, All i had to do was load the tray icon and activate it and it was up and running.

I restarted my computer for something - and NOTHING WORKS NOW!! It doesn't detect either ethernet (eth0) or wireless (eth1) and my battery indicator on the status bar (which would properly show plugged in) now shows no battery left and refuses to change to anything else.

I've been surfing this forum trying ifup -a , iwconfig, checked the interfaces file....everything looks ok...
Since I can't get that damn computer to get on the net - it's hard to post the results of these, but to summarize - nothing has let me activate the wireless or the ethernet (it just says the device does not exist) ...

I know they work - since I checked them loading XP and they were both running fine.

Any suggestions? Is the only solution a re-install?

Thanks

PK[/QUOTE]

Try a reboot. Also try installing the 686 kernel and using it.

sudo apt-get install linux-686

I once borked my 686 kernel and booted into 386 mode and it worked. should work backwards. Install that package then reboot...

---

