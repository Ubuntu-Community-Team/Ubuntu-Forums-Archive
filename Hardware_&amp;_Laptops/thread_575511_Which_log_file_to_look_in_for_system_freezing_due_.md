---
title: "Which log file to look in for system freezing due to X11 ?"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by Lars Noodén on 2007-10-14
I'm playing around with the X11 configurations to create a multi-seat workstation.  The video cards all work separately, (i.e. to a fresh install of Ubuntu 7.10 for x86 targeting that card).  

[LIST=1]
[*]00:02.0 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
[*]04:00.0 VGA compatible controller: S3 Inc. 86c764/765 [Trio32/64/64V+] (rev 54)
[*]04:02.0 VGA compatible controller: ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB] (rev 9a)
[/LIST]

However, when I try to start X using one of the other cards, the system freezes and I'm not finding any info in the log files.  e.g. if I install the system for #1 above, I cannot use #2 or #3.  If I install the system using #2, then I cannot use #1 or #3, and if I install the system using #3 above, then I cannot use #1 or #2.

Where should I be looking for clues as to the problem?

---

