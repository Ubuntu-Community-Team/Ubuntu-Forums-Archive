---
title: "hibernation doesn't work. Can size of swap be blamed?"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by kaurman on 2006-09-22
Hi,

I installed dapper on a laptop that has 1024 MB of ram. Driven by that fact, I created a 258 MB swap partition during the install. Now i am facing  a problem, that the computer doesn't hibernate. Can I blame the size of the swap partition? If so, then what should i do?
As I understand I could use gparted to change the size of the swap partition?
But when i'd delete the "old" swap then i'd have 258MBs of unpartitioned space, which (clearly?) would not be enough. I could reduce the size of the primary partition and gain some more unpartitioned space, but how could i then merge these to peaces to one whole?

How big should my swap be for hibernation to work? Or isn't the size of the swap the root of evil at all in my case?

Fixed!

---

### Post by xyz on 2006-09-23
Glad it is fixed! How about telling us how. Might help others. Thx.

---

### Post by kaurman on 2006-09-23
I just made swap big enough (the size of RAM)
The other possibility would have been using suspend2 and writing swap to a file, but i didn't want to recompile kernel and so i chose re partitioning

---

