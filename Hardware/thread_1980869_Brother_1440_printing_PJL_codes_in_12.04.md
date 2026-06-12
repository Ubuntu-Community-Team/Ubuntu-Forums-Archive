---
title: "Brother 1440 printing PJL codes in 12.04"
date: 2012-05-15
forum: Hardware
---

### Post by gbrainin on 2012-05-15
I recently upgraded from 10.04 to 12.04, and discovered a problem:

When I print things on my Brother HL-1440, it will generally print an extra page before the document I'm printing that appears to have PJL codes on it (@PJL SET SOURCETERAY=AUTO @PJL SET RESOLUTION=300).  Tried rebooting the whole system, no luck; tried searching and found no matches.

This printer worked fine under 10.04 for years, so I assume it's something that got munged with the switch to 12.04.  Any ideas?

---

### Post by gbrainin on 2012-05-16
Update: Tried switching to each of the various printer driver options with no luck.  All of them had some similar printing strangeness.  I'm now back with the recommended one (Brother HL-1440 Foomatic/hl1250), which is still sometimes-but-not-always spitting out the PJL codes.

---

### Post by gbrainin on 2012-05-26
Looks like it was a bug in the CUPS system, which has been fixed.  Marking the thread as solved.

---

