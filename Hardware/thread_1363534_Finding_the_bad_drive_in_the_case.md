---
title: "Finding the bad drive in the case?"
date: 2009-12-24
forum: Hardware
---

### Post by BigJules on 2009-12-24
Ok, my RAID 1 setup did its stuff when one of the SATA array drives failed. Simple enough to determine that it was sdb, a routine replacement/rebuild indicated. But open up the case and peer in. Just which one of those babies is sdb? Trial and error (disconnecting one by one) can give the answer but there must be a more elegant solution...

---

### Post by falconindy on 2009-12-24
The naming scheme of sda, sdb, etc is nothing but a layer of abstraction that the OS uses. There's not always a correlation between the port the drives are plugged into and the order they're assigned by the OS.

If the drives are similar aside from the serial number, then you'll need to use simple process of elimination to determine which drive the OS labelled as sdb.

---

