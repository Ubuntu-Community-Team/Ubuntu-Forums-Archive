---
title: "HP dv6000z Laptop - built-in wireless disappeared"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2007-02-07
Weird thing, I was using my laptop on my home wireless network just fine.

I then packed up the laptop in my backback and left, and when I got to my destination (which also has wireless), the wireless device was "missing" from my computer.

I first noticed that eth1 was missing, but apon further investigation, my broadcom card doesn't even show up in lspci. Ndiswraper agrees, as "ndiswrapper -l" shows that I have the bcmwl5 driver installed, but there's no hardware present. I tried uninstalling and reinstalling the bcmwl5 driver, but that (of course) didn't help...

Anyone have any ideas? I think I'm going to try to get HP to replace it.

---

### Post by ziphead on 2007-02-07
Check the wireless switch to make sure it's turned on?

---

### Post by enigma_0Z on 2007-02-07
I've tried that.

Even at that, the device *used* to show up even when the switch was off, the switch just reset the configuration and *disable* the device...

[rant]
Anyhoo, I contacted HP, and of course they said to "reinstall windows"... heh, like that's gonna help.

I did, and guess what--It didn't fix the problem!!

So I'm prolly gonna have to send the whole thing in... this really sucks
[/rant]

---

### Post by befrying on 2008-05-07
how were you able to set your wifi switch to search for networks. my laptop cant find that its using the switch

---

