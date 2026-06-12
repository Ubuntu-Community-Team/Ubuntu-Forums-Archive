---
title: "network Interface statistics reset?"
date: 2005-11-04
forum: General Help
---

### Post by webwalker on 2005-11-04
I'm a Solaris geek moving to Linux. In most of the traditional big iron Unix systems, I can run netstat -z to zero out the interface statistics to help diagnose a dicey connection, cable, port, .etc. I've found that, so far, the only way to clear the  interface in Ubuntu Linux is to reboot the machine. No user is going to let me drop-kick their machine repeatedly to test it when they're trying to work.

Is there another way in Linux to reset the interface counters? 

RMW

---

### Post by nightfly on 2005-11-07
This "-z feature" is left out intentionally from Linux network interface settings. This is to maintain status info correctness throughout the lifetime of a network link and possibly prevent against other userspace programs from reporting invalid data.

For the purpose of statistical data, you can instead record the data initially as starting data and final data and then subtract the starting data from the final data to obtain the same result as if the timers were zeroed in the first place.

I know this might be a longer process, but it is the right way nevertheless.

---

