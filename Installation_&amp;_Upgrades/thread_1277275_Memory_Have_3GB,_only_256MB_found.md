---
title: "Memory: Have 3GB, only 256MB found?"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by mrmagu on 2009-09-28
Hi,
I have an Dell Poweredge 1850 with Ubuntu 9.04(jaunty) installed (2.6.28-15).  It's very slow and I was trying to find out why when I discovered Top showing only 250332k total memory?!?  The server har 3 GB installed.

/proc/meminfo also returns: MemTotal: 250332 kB
System Monitor shows 244.5MiB

But dmidecode returns 2*1024MB + 2*512MB = 3 GB

Any clues how to make Ubuntu use the the rest of the memory?

(Attached: meminfo and dmidecode(zipped due to size))

Regards
Martin

---

### Post by kerry_s on 2009-09-28
stick them in 1 at a time, see what does not detect.
are you sure your using the right kind?

it uses PC2-3200 ECC REGISTERED 240 PIN DDR2

---

### Post by mrmagu on 2009-09-28
Forgot to mention all memory was identified/working on the server using previous operating system (windows server)

---

### Post by trundlenut on 2009-09-28
In the bios there may be a setting for OS installation which limits memory usage to 256mb, soounds like this could be turned on and causing the problem.

---

### Post by mrmagu on 2009-09-28
> **trundlenut said:**
> In the bios there may be a setting for OS installation which limits memory usage to 256mb, soounds like this could be turned on and causing the problem.

THANKS!  That was the problem!

---

