---
title: "Ubuntu in RAID?"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by elfstone214 on 2007-06-20
Hello all

I have read conflicting things regarding the use of RAID with Ubuntu. I have a motherboard with an nvidia chipset which support hardware RAID. However I have read that Ubuntu only supports software RAID through "dmraid". Am I right or can I actually run hardware RAID with Ubuntu?

P.S. I am using Feisty.

---

### Post by Syke on 2007-06-21
Are you sure it's hardware RAID? Most motherboards actually have FakeRAID which is really just software RAID. It's not easy to setup, but I think it's possible (yes, with dmraid).

---

### Post by elfstone214 on 2007-06-21
> **Syke said:**
> Are you sure it's hardware RAID? Most motherboards actually have FakeRAID which is really just software RAID. It's not easy to setup, but I think it's possible (yes, with dmraid).

trust me it is hardware RAID

---

### Post by Enverex on 2007-06-21
What motherboard is it?

---

### Post by elfstone214 on 2007-06-21
Asus P5N-32E SLI Plus

> 6x SATA 3.0Gb/s (RAID 0,1,5,10 capable) 

[http://www.tomshardware.com/2007/05/24/seven_650i_sli_motherboards_compared/page6.html](http://www.tomshardware.com/2007/05/24/seven_650i_sli_motherboards_compared/page6.html)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131153](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131153)

---

### Post by Enverex on 2007-06-21
Yeah, that's NOT hardware RAID, it's onboard software RAID, aka FakeRAID.

---

### Post by elfstone214 on 2007-06-21
> **Enverex said:**
> Yeah, that's NOT hardware RAID, it's onboard software RAID, aka FakeRAID.

alright thanks for clearing that up

I guess that leaves out raid unless I get a dedicated controller card because I cannot afford to trade cpu speed for disk transfer speeds. But even if I got a controller card, would it be supported by Ubuntu?

---

### Post by bsmith1051 on 2007-06-21
> **Enverex said:**
> Yeah, that's NOT hardware RAID, it's onboard software RAID, aka FakeRAID.
Even though it's bootable?  I thought the fact that you can boot off it (in Windows, at least!) meant that it was hw-based.

---

### Post by Enverex on 2007-06-21
> **bsmith1051 said:**
> Even though it's bootable?  I thought the fact that you can boot off it (in Windows, at least!) meant that it was hw-based.

No. You can do that with FakeRAID and hardware RAID. You're thinking of Linux software RAID.

---

