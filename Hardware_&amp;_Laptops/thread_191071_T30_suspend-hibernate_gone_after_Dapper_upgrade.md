---
title: "T30: suspend-hibernate gone after Dapper upgrade"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by woodsworth on 2006-06-07
Suspend-hibernate worked fine with Breezy, but now seems to be gone under Dapper. Where do I start?

I should mention that I upgraded by changing sources.list and using the command line, rather than install from CD.

---

### Post by woodsworth on 2006-06-07
Suspend2 wasn't working (says not compiled into the kernel?) but by tweaking hibernate.conf I got acpi_sleep to get suspend to disk and suspend to ram working, with the appropriate IBM hotkeys.

---

### Post by bakert on 2006-07-11
I have this exact problem now.  Only I don't have a hibernate.conf!

Can you tell me where I should create it or what I should install to get it?  It'd be useful to know what you did to fix this in a bit more detail if you have the time.

Thanks,

Tom

---

