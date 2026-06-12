---
title: "1 min pause while loading 8.10"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by fidgaf on 2009-01-28
I've recently upgraded to 8.10 from 8.04.

When 8.10 is loading there is a 1 minute pause (with very little, if any hard drive activity) at about 45-50% along the progress bar and then it loads just fine.

No other issues noticed but this is very annoying.

What's going on and can it be fixed?

---

### Post by LoermansA on 2009-01-28
Are you by any chance using a wireless connection? I'm experiencing the same issue whereby the bootprocess stalls at 'Configuring network interfaces' for a minute or so and then proceeds normally. I think it's just waiting for a timeout from DHCP on the wired (eth0) interface before proceeding.

Arjan

---

### Post by utter-imadness on 2009-01-28
You can see what Ubuntu is doing during boot by opening
```
gksudo gedit /boot/grub/menu.lst
```
then scrolling down to your kernel and changing it from "quiet" to "noquiet".

Now you can see exactly what Ubuntu is doing on startup. Hopefully this may help troubleshoot your problem.

---

### Post by fidgaf on 2009-01-28
Wired connection for the PC with the problem although it is a wireless box.

I'll try the menu.lst trick and get back to you.

---

### Post by avtolle on 2009-01-28
Try this; when the progress bar "stalls", press the power button once to see if it continues.

---

### Post by fidgaf on 2009-01-28
The power button idea did nothing.

It certainly seems to be a network issue.

I set menu.lst to *noquiet* and it stopped on:
[B]
Configuring network interface[/B]

I had no problems with this before and as you can see from the fact I'm posting here - there are no network/Internet issues that I know of.

I also noted that during the noquiet **mounting local filesystems** failed.

There is no evidence that there is a problem there either.

I do not know where to go from here.

---

### Post by fidgaf on 2009-01-28
Looking at the network connections it uses **Auto eth0** and is the only one present. The connection info seems to be fine and using driver **via-rhine**.

---

### Post by Xamiga on 2009-01-28
> **fidgaf said:**
> Looking at the network connections it uses **Auto eth0** and is the only one present. The connection info seems to be fine and using driver **via-rhine**.

You should always have **Auto lo**

---

### Post by fidgaf on 2009-01-28
> **Xamiga said:**
> You should always have **Auto lo**

How do I change that please?

My wireless box has a ethernet wired connection for the Ubuntu PC only. Other PCs use the wireless.

---

### Post by Xamiga on 2009-01-28
Check the /etc/network/interfaces file.

---

### Post by fidgaf on 2009-01-28
I have:

```
auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth1
```

Does that help?

---

