---
title: "hibernation problems on core duo"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by period3 on 2006-12-07
I'm running ubuntu dapper on an IBM T60, 2GHz core duo, 2GB memory.

After coming back from hibernate, the cpu throttling is all messed up.  

Sometimes, one of my cores is stuck at 2GHz, and other is stuck at 1Ghz.  Other times, they are both stuck at 1GHz.

Right now I am running both cores at full load in 'userspace' mode, but both are stuck at 1Ghz.  If I set performance mode, one of the cores goes to 2Ghz, but the other remains at 1Ghz.

When I freshly boot ubuntu, everything works properly. This only happens after a hibernate.

I am using the program CPU Frequency Scaling Monitor program that fits on my gnome task bar.  I don't know if this program is just inaccurate, or if my cores are really running at the reported speed.  

I'm also very confused by the interface: I have two icons - one per core.  Clicking one of the cores gives me a menu where i can choose 'governors' or 'frequency'.  However, the setting seems to be applied to the OTHER icon, representing the other core.  If I click that other core, I only get a menu where I can choose frequency.

---

