---
title: "Dell Inspiron 8100 Questions / Problems"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by mjwood0 on 2005-08-04
First of all, I just want to say that after trying RH, Fedora and every M$ product available, I think I've found a winner!  The support on this forum and the ease of use I've found in Ubuntu is amazing.

However, even though I have almost everything working on my Dell 8100 (more than I've had working with any other OS), there are still a few annoyances that I was wondering if the good people here could help me with.

My current setup is as follows:
   Intel Pentium 3 1.2GHz processor
   256 MB RAM
   1600X1200 UXGA+ Screen (beautiful)
   Nvidia GForce2Go 32 MB video
   Linksys WPC54G Wireless (via Ndiswrapper works great)
   Dual booting with XP Pro till I can get Cisco VPN working under Linux (necessary for work).

My problems are as follows:

1. I have a mouse / keyboard stuttering issue.  People say to disable powernowd to get rid of this issue. (Note: it also seems that my internet stutters with the keyboard / mouse)  Since I mainly use this laptop on battery, it would be nice not to have to disable the processor throttling if at all possible.  Any ideas or solutions?

2. I successfully installed the nvidia drivers and am getting great performance (thanks to this site).  But now my suspend / hibernate don't work.  Instead of turning off the display, it stays on and nothing seems to happen (or else it resumes right away).

3. With the open source nv driver installed, I could suspend.  But when I resumed, my wireless was all messed up.  I think it's an ndiswrapper issue, but how do I go about fixing it?

Thanks so much for all the help and for reading this long post!  Hopefully I'll be able to contribute in the future!

---

### Post by dpb on 2005-08-09
[http://www.ubuntuforums.org/showthread.php?t=28372&page=2&pp=10&highlight=dell+8100](http://www.ubuntuforums.org/showthread.php?t=28372&page=2&pp=10&highlight=dell+8100)

FYI -- In the above thread I found my answer.  Turn off powernowd.  Try using a different frequency scalling system.  I am currently using klaptop (combined with acpi).  However I guess there are ones that operate in the kernel as well maybe independent from acpi.  

If you can confirm that shutting down powernowd clears the problem, start looking into a way to enable an alternate scalar.

/db

---

