---
title: "Laptop restarting randomly"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by jim78 on 2008-01-02
Hi all,
           My e-system laptop (with dapper) keeps randomly restarting. Everything is fine until it shuts down and fine when it starts back up again. i don't use the battery most of the time when i'm at home and thought it might  have something to do with power management, so i changed the battery option  setting to "do nothing" when critical. THis apparently hasn't solved the problem. The laptop doesn't seem to be overheating either. I have no idea what it could be. Anyone have any suggestions?

Cheers,
               James.

---

### Post by ARhere on 2008-01-02
I will try to help, but I need to know if the laptop is shutting down ([i]you see the Linux OS running its shutdown script[i]) or is it just kicking off?

If it is just kicking off, it can be two things.

1.  E-machines are known for cheap hardware design to save money.  Check to see if your battery is loose.  It could be breaking its contact when bumped.

2.  Battery management has to be "learned" by the laptop in most cases.  This means the battery state is not really reported well by the hardware in the battery.  To fix this, charge your battery fully for 24 hours with the laptop off, then turn the laptop on and let it drain till dead.  Once, maybe twice of that should fix things.  There might be a "Battery Calibration" option in the Add/Remove section as well.

If it is rebooting, well..... not sure.  But more info is needed.

-AR

---

### Post by jim78 on 2008-01-02
Hi,
     I've not actually had the battery in at all since i re-installed ubuntu a month or so back as I rarely move the laptop from my desk. I have a Dell that I cart about with me so I don't really need the battery at all for the e-system. 
   As far as I can tell it's just kicking off not shutting down. I've turned all the battery monitoring/power settings I can find to "do nothing" or "never" for hibernating or shutting down when battery power is low.

---

### Post by lisati on 2008-01-02
> **jim78 said:**
> Hi,
     I've not actually had the battery in at all since i re-installed ubuntu a month or so back as I rarely move the laptop from my desk. I have a Dell that I cart about with me so I don't really need the battery at all for the e-system. 
   As far as I can tell it's just kicking off not shutting down. I've turned all the battery monitoring/power settings I can find to "do nothing" or "never" for hibernating or shutting down when battery power is low.

There could be an intermittent fault in your power lead or connectors.

---

### Post by ARhere on 2008-01-02
> **lisati said:**
> There could be an intermittent fault in your power lead or connectors.

Agreed.  I would _not_ leave the battery unconnected.  Those power connectors are really easy to wiggle loose, I know because I design small scale power supplies and those connectors are really bad!  Without the battery in place, there is no backup if this happens.  The reason you do not see this with a desktop is the connections from wall power to machine are made to be more sturdy **and** you have enough capacitance to handle a quick voltage transient.

Plug the battery in even if it is plugged into the wall.

-AR

---

### Post by jim78 on 2008-01-02
hi,
      thanks for the replies. yeah i guess that makes sense about the wall to laptop power connection not handling the odd voltage change. At least with the battery in i'm backed up. Thinking about it a bit more I did have the same problem running XP so it can't be a software/setting issue.

---

### Post by ARhere on 2008-01-03
Can you please consider marking this post as [solved] if your problem is fixed?

Thanks,
-AR

---

