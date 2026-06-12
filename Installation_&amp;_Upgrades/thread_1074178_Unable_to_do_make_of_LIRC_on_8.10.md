---
title: "Unable to do make of LIRC on 8.10"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by nicoloks on 2009-02-18
Being a fairly new user to Linux I have what seems like a really weird problem. I've uninstalled lirc 0.8.3 from my Mythbuntu 8.10 (fresh install with only updates applied), and checked out the latest version of lirc from CVS.

I can do autogen, setup and configure, however when it comes to doing the make I get this error;

> ERROR: Kernel configuration is invalid. include/linux/autoconf.h or include/config/auto.conf are missing. Run 'make oldconfig && make prepare' on kernel src to fix it.

I've tried running make under sudo, but still no cigar. I've also verified that autoconf.h and auto.conf do exist in /usr/src/linux-headers-2.6.27-11-generic/include/linux and /usr/src/linux-headers-2.6.27-11-generic/include/config respectively. "uname -r" gives me "2.6.27-11-generic", so they are in the correct location.

The really weird thing is that I build an almost identical Mythbuntu box last week using the exact same process without a hitch. I know it was exactly the same as I copy and pasted all my commands from the last box I built into a text file so I could follow it easily this time around.

Long story short, would I be right in thinking there is some sort of "undocumented feature" that has been introduced into the lirc CVS in the last week, or have I managed to miss something here?

---

### Post by nicoloks on 2009-02-18
Definately an issue with the lirc source I got from CVS today. Luckily I didn't remove the lirc source from the machine I built last week. Copied that to the new machine, followed the same process as mentioned above, and it installed fine.

---

