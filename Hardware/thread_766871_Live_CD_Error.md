---
title: "Live CD Error"
date: 2008-04-25
forum: Hardware
---

### Post by simonpearson on 2008-04-25
I have just created a CD from the Hardy Heron iso, which I downloaded today. 

On startup it prompts me for language selection, then I chose the "Start or Install" option (or whatever its called in 8.04!).

Straight after the Linux compression dialog has finished, I get the following two errors:

[ 64.324025] ACPI: EC: acpi_ec_wait timeout, status=0, expect_event 1
[ 64.324086] ACPI: EC: read timeout, command=128

I am trying to run this on a Sony Vaio VGN-FE41M, which has happily run 7.10 and 7.04 live cd's before.

Anyone with any ideas?

---

### Post by dstew on 2008-04-25
Try the kernel parameter **acpi=off**. To add this parameter to the kernel line, press F6 at the opening menu.

---

