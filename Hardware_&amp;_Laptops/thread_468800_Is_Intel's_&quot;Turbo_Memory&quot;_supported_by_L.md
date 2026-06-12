---
title: "Is Intel's &quot;Turbo Memory&quot; supported by Linux?"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by kebajonathan on 2007-06-09
Hi,

I'm interested in the new Lenovo Thinkpad T61 ([thinkwiki.org]("http://www.thinkwiki.org/wiki/Category:T61"); Announcement in German [by IBM]("http://www5.pc.ibm.com/de/products.nsf/$wwwPartNumLookup/_ND218GE?OpenDocument")) so I'm wondering whether Intel's new "Turbo Memory" ([Intel announcement]("http://www.intel.com/design/flash/nand/turbomemory/index.htm"); [Wikipedia]("http://en.wikipedia.org/wiki/Intel_Turbo_Memory")) is supported. Do you know anything? What about the graphics chipsets?

Thanks for answers.

---

### Post by muximus on 2007-06-12
i dont think you need to worry.. if it is intel, they probably would open the source for this.., if not, they would definitely provide linux support
both the graphics chipsets are supported.. intel drivers are open source, nvidia closed source drivers are available for linux

---

### Post by slade on 2007-07-19
does anyone know for sure?  its not just an issue of whether or not there's a linux driver, but whether or not linux actually makes use of it.  I'm getting a new laptop soon and wondering if I should get this or not.

---

### Post by ramjet_1953 on 2007-07-19
It may be worth dropping an email to Intel and ask them.

Regards,
Roger 8)

---

### Post by nedkelly on 2008-01-11
As far as I can se, it is not, but have not tested this, so I do not know for sure

[http://www.thinkwiki.org/wiki/Intel%C2%AE_Turbo_Memory_hard_drive_cache]("http://www.thinkwiki.org/wiki/Intel%C2%AE_Turbo_Memory_hard_drive_cache")

---

### Post by Yellow Pasque on 2008-01-11
I'm guessing it would work fine, as long as the memory is viewed abstractly as HD cache and the details are taken care of in the hardware and BIOS. In other words, the OS should be able to access the disk through the SATA (PATA?) interface like usual.

---

### Post by neodarksaver on 2008-03-29
it is not supported. readyboost and readydrive are both vista only features... intel built this thing to suppose those two... but hopefully there will be some future use for this thing in ubuntu.

---

