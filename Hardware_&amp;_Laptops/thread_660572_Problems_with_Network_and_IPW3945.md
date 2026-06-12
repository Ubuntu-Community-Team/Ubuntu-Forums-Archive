---
title: "Problems with Network and IPW3945"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by godzirra on 2008-01-06
Hey folks.  I'm running 7.10 on an hp DV6500, and at random times, my network drops.  The only difference I can tell when my network drops is the ipw3945 module lists "0" under the "used" category.  When this happens, I can't do anything really other than do a hard power down of my laptop.  What's going on here, and how can I fix it?  I  can't run anything sudo, and I've tried                   removing and reloading the module in a window that I already had "sudo su -"'d but it still doesn't allow me to connect to the network afterwards.  I'm using the restricted drivers for intel 3945. 

And yes, I tried looking at the other posts first. ;) 

Anyone have any ideas?

Thanks!

---

### Post by mybeat on 2008-01-06
**This post could be related to an Ubuntu bug filed at**:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109887](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109887) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Alot of people are having the same problem
go check that bugs.launchpad.net link

---

### Post by godzirra on 2008-01-06
Is there anywhere that dmesg is logged so I can look at my past ones to see if that is indeed the problem?

---

### Post by mybeat on 2008-01-06
There should be dmesg.0 dmesg.1 dmesg.1gz etc.. in /var/log

---

### Post by godzirra on 2008-01-07
> **mybeat said:**
> **This post could be related to an Ubuntu bug filed at**:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109887](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109887) [br].



Yeah, this is exactly my problem.  Thanks.  I'm checking out the hardy alpha 2 livecd now to see if it resolves the issue or not, since they said it won't be fixed in gutsy.

---

