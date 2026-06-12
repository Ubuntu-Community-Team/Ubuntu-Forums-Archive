---
title: "Can't find sd card after jaunty install on 2 eeepcs"
date: 2009-09-20
forum: Hardware
---

### Post by pollywog on 2009-09-20
I've installed jaunty on 2 different eeepcs, one a 900, the other a 1000he. Neither of these systems seem to recognize the sd card. I've tried the Array.org kernel as well as the generic, no difference. I've tried fdisk -l, and I see no entry corresponding to the card. Likewise gparted doesn't seem to see it either. Any ideas?

---

### Post by HankB on 2009-09-21
> **pollywog said:**
> ... Any ideas?
See what 'dmesg' reports after you insert the card. It might provide a hint as to what is going on. Posting any suspicious output here might help someone to point out the problem.


HTH,
hank

---

### Post by pollywog on 2009-11-16
I hate to admit this, but I just realized that these things come with a blank SD card. With an actual SD in place both work like a charm. OOPS!

---

