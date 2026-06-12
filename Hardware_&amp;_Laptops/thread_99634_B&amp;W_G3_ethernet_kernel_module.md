---
title: "B&amp;W G3 ethernet kernel module?"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by etyrnal on 2005-12-05
Hello,

please let me say right up front that i have ulterior motives...

i have two questions (at least i think).

1.) From the LiveCD, is there a way to determine, using standard tools, exactly which kernel module has been loaded to support the ethernet port on the Blue and White G3 Macintosh PPC ??  

2.) would it be possible to copy that kernel module into the iso of the PPC gentoo so that i can get gentoo installed on my B&W G3?  (i HAVE to use gentoo for work) I noticed that they both use the Elf32 kernel.

sorry about the ulterior motives, but i can't use ununtu.  i'm trying to learn to be more useful at work, and all of the servers run gentoo (not my decision)...  so i am trying to get gentoo ppc going on my Yoesmite (B&W G3) so i can study up on my own time, and experiment w/ out destroying anything at work =)

or is it possible i could just find out which driver that is included w/ gentoo is the right one?  

thanks, and i hope i have not insulted any overly-sensitive individuals.

---

### Post by hw-tph on 2005-12-06
"bmac" is the name of the driver for the onboard Ethernet device on the Yosemite. Just use **modprobe** to load it, i.e. **modprobe bmac**.


Håkan

---

