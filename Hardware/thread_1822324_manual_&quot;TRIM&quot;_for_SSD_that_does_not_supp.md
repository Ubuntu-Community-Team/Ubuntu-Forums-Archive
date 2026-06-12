---
title: "manual &quot;TRIM&quot; for SSD that does not support TRIM?"
date: 2011-08-10
forum: Hardware
---

### Post by poikiloid on 2011-08-10
I have an older netbook (Asus EeePC 1000) with miniPCIe SSD storage (which I think emulates PATA or SATA with passthrough).

The SSD controller firmware does not support TRIM.

Is there any way to write 1's to free blocks and inform controller of this, so it doesn't have to clear blocks before writing to them, in effect doing what TRIM would do?  I have heard of people doing things like this on Windows ("Tony-TRIM"). Wondering if any way to do for Linux. I am aware of hdparm's wiper script, but I think that still requires actual TRIM-enabled SSD to work.

---

### Post by psusi on 2011-08-10
No.  The best you can do is use hdparm to security erase the entire drive, and start over.

Also leave a gb or two of the disk unpartitioned and this will have much the same effect that TRIM would anyhow by making sure that there are always some free erase blocks that have never been written to.

---

