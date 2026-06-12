---
title: "Process given access only to a limited fraction of RAM"
date: 2013-01-07
forum: Hardware
---

### Post by abhicr on 2013-01-07
Hello there,

I'm a novice, using 12.04LTS with dualboot on my Sony Vaio VPCEH laptop (i3, 4Gigs of RAM, 4Gigs of swap).

I'm running a few data analysis programs that are computation intensive. However, the results took longer than i expect. It was completed in half the time on a machine with 2Gigs of RAM, which i found a bit odd. When I checked the resource allocation using both the "top" command and using the htop tool (from synaptic), both showed that RAM allocation is frozen at 35% for that process, despite the swap space being sparsely used. This did not happen in the 2Gigs machine, and RAM was frequently dumped into the swap area. I'm not aware of what's happening. Neither do I know what information I'll have to provide in this regard.

I'd be glad if help comes in time... Please let me know what is it that you'll need to help me... 

-abhi

---

### Post by grahammechanical on 2013-01-07
> RAM allocation is frozen at 35% for that process

35% of what? Of 4GB. Which is 1.4GB if my calculations are correct. Are we comparing like for like? What CPU does the 2GB machine have? The 4GB machine does not need to use swap. Whereas, the 2GB machine does need to use swap.

Perhaps you are seeing a limitation of the data analysis program? Does the 2GB machine have a multi-core CPU? Perhaps the analysis program cannot make use of a multi-core CPU.

If the analysis is "computation intensive," then that is more a function of CPU ability than the amount of RAM. It is true that in some cases more RAM is better than less RAM but in this case double the RAM does not necessarily mean half the time. I think other factors are involved.

Regards.

---

