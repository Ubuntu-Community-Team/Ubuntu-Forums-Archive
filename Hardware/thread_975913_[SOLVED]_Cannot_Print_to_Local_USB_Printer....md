---
title: "[SOLVED] Cannot Print to Local USB Printer..."
date: 2008-11-08
forum: Hardware
---

### Post by MikeTheC on 2008-11-08
Hey Folks:

I've been looking around, and while I see similar threads, it appears they either are for completely different printers than what I have, or they're being shared on a network.

**CONFIGURATION:**
Host OS: **Ubuntu 8.10 32 bit with latest updates**
Host Box: **AMD Athlon 3800+, 2GB RAM**
Printer: **Canon S820** (inkjet)
Connectivity: **Local USB port**

**Symptomology:**

Preface: This printer worked perfectly on earlier versions of Ubuntu, and just worked a couple weeks ago when I still had 8.04 installed.

When I try to send any print job to this printer, it "instantly completes" and nothing is ever printed. Like others have described in other threads vis a vis SAMBA-connected printers, the printer is obviously communicated with by the host system, initializes and/or primes itself (depending on it's idle period).

**(Failed) Resolutions Attempted:**

1. Recycled printer.
2. Reinstalled driver.


Obviously the printer works, and obviously the cabling and hub are all fine (since the printer initializes itself). And clearly this problem must be at least somewhat systemic given that the same symptomology is present on other brands of printers, and networked (vs. local) connections.

Thanks much in advance!

---

### Post by MikeTheC on 2008-11-13
I found out that the problem is actually within Scribus somewhere. When I print pretty much in anything else I've tried (Firefox, Inkscape, Gimp, etc.) there's no problems at all.

:guitar:

---

