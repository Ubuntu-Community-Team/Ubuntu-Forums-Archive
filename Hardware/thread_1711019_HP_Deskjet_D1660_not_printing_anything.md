---
title: "HP Deskjet D1660 not printing anything"
date: 2011-03-20
forum: Hardware
---

### Post by epp on 2011-03-20
I recently purchased a new HP Deskjet D1660 printer and it will not print anything with Ubuntu.

Per the HPLIP web site, it is fully supported beginning with HPLIP version 3.9.8, the version installed is 3.10.2.

HPLIP is recognizing the printer as it's listed in the HP Device Manager, but when printing anything, including a test print sent via the Device Manager or from the CUPS interface directly, nothing prints - the printer does absolutely nothing.

Are there any known issues with this particular printer?

Thanks in advance.

**Changing the PPD file from the D1660 "hpijs" to the D1600 "hpcups" was all that was required.  Once this change was made, the D1660 began to print.  :)**

---

