---
title: "SATA AHCI hot plug no longer working in newer releases"
date: 2020-01-30
forum: Hardware
---

### Post by ideasman69 on 2020-01-30
Hi guys,

I've been running ubnutu 16.04LTS for a while on two asrock J3455 motherboards. One of the main things i do is hot plug SATA drives which has always worked in 16.04 (and mint 19.x).

However - after upgrading to 18.04 and a subsequent clean install of 18.04, SATA hot plug doesn't work on the intel SATA ports anymore - although it does work on the ASMedia SATA ports.

Figured I'd upgrade to 19.04 and found that hot plug doesn't work on any of the ports!

So I went back to 18.04, downgraded the kernel to 4.15 and still no go.

Is there a setting or module or something that needs to be re-enabled for hot plug to work? Both motherboards have AHCI + hot plug enabled on each port, but it's baffling me that this isn't working on newer releases.

Any thoughts or advice?

Cheers!

---

