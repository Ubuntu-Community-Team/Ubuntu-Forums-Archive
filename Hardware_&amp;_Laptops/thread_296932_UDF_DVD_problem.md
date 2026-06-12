---
title: "UDF DVD problem"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by Exxar on 2006-11-10
I'm running Dapper on a laptop and my Matsushita UJDA740 CD-RW/DVD-ROM is acting funny. It cannot read any UDF DVDs I insert. The Device Manager correctly detects the volume name, but the DVD doesn't seem to get mounted. When I do ls /media/cdrom0/, nothing gets listed.

All other DVDs and CDs work normally.

---

### Post by tonyr on 2006-11-10
Packet-writing support (udf) is not in Dapper by default. Support is
available with the **udftools** package. Read-only
support seems to be present in Edgy.

---

