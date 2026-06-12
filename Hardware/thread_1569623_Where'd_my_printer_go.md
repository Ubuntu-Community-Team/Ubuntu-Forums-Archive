---
title: "Where'd my printer go?"
date: 2010-09-07
forum: Hardware
---

### Post by awacs on 2010-09-07
Existing Lucid box; root HD died, new install on another disk. The parallel printer (HP LJ 5 on parallel port off the system board) is no longer recognized:

# dmesg|grep lp
...
[   33.256027] lp: driver loaded but no devices found
...

lp, parport, ppdev modules loaded. Oh noes! What do I do?
Cable connection is nice and tight - took it off and reinstalled anyway. BIOS stuff shows to port enabled. Now what?

Thanks!

---

