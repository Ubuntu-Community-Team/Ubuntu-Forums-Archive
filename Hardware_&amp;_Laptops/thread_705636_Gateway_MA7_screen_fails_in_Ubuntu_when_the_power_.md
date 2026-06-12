---
title: "Gateway MA7 screen fails in Ubuntu when the power cord is disconnected."
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by emergingtechnologies on 2008-02-23
I promise I have searched all over for this particular problem but I can't find a similar issue mentioned.

This is with the Gateway MA7 -- worked perfectly with Ubuntu 7.04 -- but after I upgraded to 7.10 I ran into this weird situation where I cannot use the Laptop unless it is plugged in.

If I unplug the laptop the screen will fail.  I can see sort of the ghost of what is going on on screen very faintly but it's impossible to work on... the screen has essentially gone black.

Any ideas?  Thanks.

---

### Post by emergingtechnologies on 2008-03-03
Any ideas at all?  Thanks.

---

### Post by DanaG on 2008-03-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/121833) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hmm, I had that issue on my M685 (also known as PA6).  It turns out that the backlight was simply turning entirely off when gnome-power-manager tried to dim it.

---

### Post by emergingtechnologies on 2008-04-02
HARDY HERON solves this problem!  The problem is gone.  Order is restored!

---

