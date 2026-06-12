---
title: "RAM Support Legacy vs. Ubuntu"
date: 2015-06-25
forum: Hardware
---

### Post by Idjit_BoB on 2015-06-25
I have a few questions regarding BIOS (and Ubuntu) when upgrading the memory slots to their maximum as recommended by the manufacturers.

PART 1
I installed a RAM upgrade to the maximum (2GB, 1GB/slot) on my old Sony laptop. I did not act quick enough on start up to get into the BIOS configuration menu. I noticed that Linux recognized the upgrade. Does this really matter when using Ubuntu? Do I need to change my BIOS settings?

PART 2
My other laptop (Thinkpad T42) has 2 memory slots with a maximum of 2GB RAM (1GB/slot) support.

Is this a physical or BIOS limitation?

Is it possible to install 4GB RAM (2GB/slot)?

Will Ubuntu recognize it and use it?

Thanks in advance.

---

### Post by weatherman2 on 2015-06-25
1. Your BIOS will automatically recognize whatever RAM you have installed - you do not need to do anything or tell it to look for more RAM.  Yes, Ubuntu or any OS will automatically see it (at least, up to 4GB, then there may be complications depending on a few things.  For 2GB, no issue at all.).

2. The "physical limitation" is actually with the chipsets and the hardware, not the BIOS, which is designed based on the hardware.  Occasionally a BIOS when originally created could recognize only some maximum amount of RAM - say when your laptop came out, there were only 512MB SO-DIMM sticks available so the BIOS might only expect a maximum of 1GB, but later 1GB sticks became available, so an updated BIOS might be needed so the BIOS will know about all current compatible sizes of RAM.

But usually, the real limitation is with the hardware, not the BIOS.  If a chipset can address a maximum of 2GB of RAM, you can't use more than that.  PERIOD.  No BIOS update will help you, even if you can find bigger RAM sticks that fit into those slots.

Find out what the maximum amount of RAM is for your Thinkpad.  It may vary even by submodel.  As I recall, there are a lot of different versions of those Thinkpads, even "T42" may mean numerous different models.  Not sure.  You can try [www.crucial.com](www.crucial.com) and plug in the info to see what type of RAM they recommend, what the maximum would be.

---

### Post by Idjit_BoB on 2015-06-26
weatherman2

Thank you for answering my question. A concise but thorough answer. You hit the mark and I can't think of any follow up questions.

I will try the website you recommend.

Best Regards
Idjit

---

### Post by Idjit_BoB on 2015-06-26
weatherman2,

I went to the crucial website as you suggested, and plugged in the information they required. I found that I am limited to the manufacturers recommendation on both my laptops.

So now as I think about it, I do have a follow up question which you may have already answered. So I am looking for some clarification is all. You alluded that the issue is physical since you said the "limitation is with the hardware".

Are firmware updates available for chipsets which may resolve the memory size limitation?

---

### Post by weatherman2 on 2015-06-26
Unfortunately, no - there is no way to upgrade a chipset to allow for more memory.  The limitations are part of the hardware.

---

### Post by Idjit_BoB on 2015-06-26
Thanks again. You have been very helpful.

---

### Post by Yellow Pasque on 2015-06-26
> **Idjit_BoB said:**
> Are firmware updates available for chipsets which may resolve the memory size limitation?

Sometimes, the BIOS does not support the maximum memory allowed by the chipset (or the CPU in the case of newer CPU's which have an integrated memory controller), and there may be a BIOS update to allow it.
The Thinkpad T42 is not such a system. It has an Intel 855PM chipset, which only supports 2GB max.

---

### Post by Idjit_BoB on 2015-06-27
Thanks Temujin.

---

