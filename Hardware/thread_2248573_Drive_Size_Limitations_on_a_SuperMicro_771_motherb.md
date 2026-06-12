---
title: "Drive Size Limitations on a SuperMicro 771 motherboard?"
date: 2014-10-15
forum: Hardware
---

### Post by Derek_Gentle on 2014-10-15
Hello All

I am in the process of rebuilding one of my servers as the motherboard gave out.
I have a spare SuperMicro X7DVL-i that has 6 SATA2 connectors on it:
[http://www.supermicro.com/products/motherboard/Xeon1333/5000V/X7DVL-i.cfm](http://www.supermicro.com/products/motherboard/Xeon1333/5000V/X7DVL-i.cfm)

As you can see from the layout, the PCI-e connector is in a very, and I do mean *very* awkward position.

What I need to know is if there are going to be any problems connecting 3TB drives to the SATA ports, and have them recognized as such?
While I have an LSI HBA that supports the 3TB drives, but due to the location of the PCI-e slot, I don't actually have any way to use it.

thanks in advance!

---

### Post by weatherman2 on 2014-10-15
I wouldn't be worried about it.  I think the issue is with GPT partition tables (which you want for large disks) vs. MSDOS partition tables.  I've not had any trouble connecting 4TB drives to even some older machines' SATA ports.

---

### Post by Derek_Gentle on 2014-10-16
Thanks!

---

