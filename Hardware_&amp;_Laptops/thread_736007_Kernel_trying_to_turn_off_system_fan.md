---
title: "Kernel trying to turn off system fan???"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by NeatO7364 on 2008-03-26
Hi all,

I have been using Ubuntu for almost 6 months now on an Intel Celeron computer (about 4 yrs old) and it has served as a rock-solid server.  However, I recently began having a strange error in which the kernel appears to be trying to turn off the computer's one internal fan (it's in a micro-ATX enclosure, but yeah, still probably not the best idea when it comes to heat dissipation).  The biggest problem is that the kernel is trying to do this multiple times per second and I'm using logcheck to keep an eye on my system logs, so I get emails that are approximately 70,000 lines long (not an exaggeration!).  Furthermore, I believe that the kernel is using up resources like crazy, and the system locks up for about 10 seconds at a time while this is happening.

Here is a VERY brief snippet of what I'm getting:

Mar 26 00:26:00 axs kernel: [13246.552593] ACPI: Transitioning device [FAN1] to D3
Mar 26 00:26:00 axs kernel: [13246.552603] ACPI: Transitioning device [FAN1] to D3
Mar 26 00:26:00 axs kernel: [13246.552607] ACPI: Unable to turn cooling device [e6aa82a0] 'off'

Why is the kernel trying to turn the CPU fan completely (D3!) off?  I had read elsewhere that a kernel update fixed the problem, so I went ahead and did a complete system upgrade to the latest stable Ubuntu 7.10 but I'm still getting this crazy error.  Would moving the system to a more modern motherboard and possibly larger case (with more fans) help?  

Thanks in advance for any and all advice!

--Avi

---

