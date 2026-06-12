---
title: "Ubuntu has 25% less battery-life compared to other Linux-Distributions"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by schmolch on 2007-04-22
This is not meant to be a rant or provocative post, i installed ubuntu 7.04 yesterday and like it very much.

Unfortunately though my Laptop (Thinkpad CoreDuo) requires 20W now beeing idle, while running Gentoo-Linux its only using 15W.

Now what could be the reason for this?

The CPU speedsteps fine, is at 1GHz when idle.
BusMasterActivity of both cores is 0 when idle and it goes into C3.

wlan power-management is set to the same level (7), which i did manually with iwpriv.

laptop-mode for the hdd did not work initially, the init-script gives an error, but when the hdd shuts down for a while the power-usage drops to 18.5W, thats still too much though.

Does anyone have an idea what could be causing this power-drain?

I suspect it must be cpu-related since the temperatures are also higher then they are supposed to be.


schmolch

---

### Post by moixa on 2007-04-22
you need to explicitly enable laptop mode in /etc/default/acpi-support

---

### Post by schmolch on 2007-04-22
thx

---

### Post by ntetreau on 2007-04-23
It turns out laptop-mode won't be started if you boot up unplugged, I wrote a howto to enable it and also to use the power management features on your wifi card if it's an intel:

[http://ubuntuforums.org/showthread.php?t=419772](http://ubuntuforums.org/showthread.php?t=419772)

Nic

---

