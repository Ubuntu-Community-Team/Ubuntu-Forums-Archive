---
title: "Lenovo 3000 N200 keyboard problem (no PgUp/PgDn/Home/End)"
date: 2013-10-19
forum: Hardware
---

### Post by onebir on 2013-10-19
Xubuntu 13.04 installed without a hitch... except this one:
The PgUp/PgDn and Home/End keys (=Fn+PgUp/PgDn) don't work.
A little searching suggested diagnostic tools: xev and acpi_listen:
**- xev** doesn't detect any events from Fn or PgUp/PgDn. (But it does detect the other keystrokes.)
- **acpi-listen** doesn't detect any events from Fn or PgUp/PgDn. (But it does detect the acpi relevant ones, eg screen brightness changes)
- the volume +/- and brightness +/- keys are Fn+F1/F2/F10/F11 respectively, and work fine. So **Fn is being recognised somewhere**. 

Any troubleshooting &/workaround suggestions gratefully accepted - thanks :)

---

