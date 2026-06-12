---
title: "USB to Parallel Adapter for printer not detected?"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by Hubris2 on 2006-12-31
I have a Brother HL720 printer that is connected via an HP branded USB2 to parallel port adapter.  The printer is in the CUPS database, but how do I set things up so the system knows how to access it?  The printer is not automatically detected.

The cable is marked as UP-11128EH.
The device is seen in the list of USB devices...

Bus 001 ID 3980:0002

When I try add the printer manually I have a port named "hp no_device_found".  Is that standard, or has it detected my adapter but doesn't know what to do with it?

Does anybody have any ideas?

Thanks!

---

### Post by connan1973 on 2007-03-18
Set as USBPARALLEL , and device as DEVICE....

---

### Post by Hubris2 on 2007-03-18
Set....where?  I don't see any configs that appear to use that syntax...

---

