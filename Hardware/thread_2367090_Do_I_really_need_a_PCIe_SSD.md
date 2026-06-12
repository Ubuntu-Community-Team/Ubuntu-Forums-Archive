---
title: "Do I really need a PCIe SSD ?"
date: 2017-07-25
forum: Hardware
---

### Post by automate-stuff on 2017-07-25
Hi, I am a programmer and I am upgrading my laptop's HDD to an SSD, I run multiple IDEs , PDF readers , Browser instances + tabs and etc...Now Should I buy a PCIe SSD or a SATAIII SSd? I have an M.2 Connector on the motherboard that supports both...Is there a difference for what I want to do between the two types of SSDs ?

---

### Post by TheFu on 2017-07-25
If you want the fastest, the 16x PCIe NVRAM storage devices are 10x (or more) faster than m.2 or SATA connection allow.  32Gbps is pretty fast. Don't think any laptops can handle that, so you might be stuck with the 3.2Gbps Samsung stuff.

Do you need that?  It depends.  My "power" laptop doesn't have any SSD and I do development on it all the time.  So, it depends on the sort of development you do and how sensitive it is to I/O waits.  Since I do web-app development and the back ends we use don't have SSD storage, it is better for me NOT to have it to see how things work.  But if I were doing C++ development still and compiling 400+ classes daily, you bet I'd get the fastest storage I could afford.  I did some math comparing developer productivity between IDE and SCSI storage in the late 1990s.  The SCSI storage was 3x more expensive, but allowed 3 extra compile/link rounds per day.  It was clearly worth it.  2 weeks later the Adaptec 1940u cards arrived and we started installing them with the fresh 80G SCSI HDDs (available then).  Devs were happier. Management was happier.  Everyone seemed more productive.

You probably want the [Samsung 960 Pro - NVMe PCIe]("https://www.amazon.com/Samsung-960-PRO-Internal-MZ-V6P512BW/dp/B01LXS4TYB/"), if that fits your laptop.

---

