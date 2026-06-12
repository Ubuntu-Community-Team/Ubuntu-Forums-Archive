---
title: "SuperMicro SuperServer 6010H"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by bgearig on 2007-10-26
Our company started off with a SuperServer5010E BackupBox.  However it crashed and we ordered a SuperServer6010H but we had to have a Backup System in place while we waited on it's arrival.  So I performed a fresh install of Ubuntu 7.10 with BackupPC3 on an old HP Vectra machine.  Everything worked great.

Today our new SuperServer 6010H arrived and I just transferred the HDDs over into the new box (Never had a problem while doing this with Ubuntu before).  Now when it boots up (or tries), I get the following on my console:
 
 * Loading hardware drivers...
[  106.905138] agpgart: TLB post flush took more than 3 seconds
[  109.913876] agpgart: TLB Dir flush took more than 3 seconds
[  109.914040] agpgart: Serverworks CNB20HE is unsupported due to lack of documentation.
[  109.914109] agpgart: Serverworks CNB20HE is unsupported due to lack of documentation.

 * Setting the system clock
 * Loading kernel modules...
 * Loading manual drivers...


And then nothing else happens...

Any ideas?

---

