---
title: "problem with idle=poll"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by insulae on 2007-11-20
hi, i have a notebook Compaq Presario V3415LA, if i try to use GNU/Linux the notebook crash, if i pass the parameter idle=poll to the kernel the notebook work perfectly.
so where is my problem?, my battery have a duration of 3 to 4 hours and with this parameter the battery duration is the 2 hours.
i found this in kerneltrap.org

> 
Format: idle=poll or idle=mwait
+                       Poll forces a polling idle loop that can slightly improves the performance
+                       of waking up a idle CPU, [B]but will use a lot of power and make the system
+                       run hot[/B]. Not recommended.
+                       idle=mwait. On systems which support MONITOR/MWAIT but the kernel chose
+                       to not use it because it doesn't save as much power as a normal idle
+                       loop use the MONITOR/MWAIT idle loop anyways. Performance should be the same
+                       as idle=poll.

so what parameter i can use to try a replace to idle=poll ? any idea?

Grettings
insulae

---

### Post by insulae on 2007-11-28
ok! the solution is: Ubuntu Gusty 7.10 in 64bits mode, with 64bits i don't have any problem, everything work perfectly.
For spanish user i made a installation howto for the laptop Compaq Presario V3415LA, V3315LA, F-565 and V3418LA, you can see the howto here:

[http://www.insulae.com.ar/view.php?page=SL_HowtosD002](http://www.insulae.com.ar/view.php?page=SL_HowtosD002)

Grettings
insulae

---

