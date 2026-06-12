---
title: "Sure way to see hardware properties?"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by 1002285 on 2007-02-26
Please tell me if there is a sure way to get to know a computer's hardware properties.

I just bought (haven't finalised the deal, fortunately) an HP nx9005 laptop from an auction (like Ebay). It was supposed to have 2 GHz AMD Athlon Mobile 2600+ processor and 512 Mb RAM.
In Windows Control Panel's System Properties I found that it has 1 GHz processor and 448 Mb RAM. Later it "updated" the information to 1,99 GHz for the processor, but the number of RAM is still 448.
How can I be sure about the RAM? Can I look at it using Ubuntu Edgy or Dapper CD without installing on the harddrive? I also have Sytem Rescue CD, for example.
Thanks very much for anybody who can give any advice.

---

### Post by chewearn on 2007-02-26
The 448MB simply means 64MB is used by your graphics (due to shared memory).

---

### Post by 1002285 on 2007-02-26
> **AstalaVista said:**
> The 448MB simply means 64MB is used by your graphics (due to shared memory).

Thank you very much. I did not even think that 2600 means 2,6 G, but I was just wandering, whether Windows's system properties was reliable.

You are sure about the shared memory? Even with a separate graphics card (ATI Radeon)?

---

### Post by chewearn on 2007-02-26
Most of the time, motherboard which has on board graphics (like notebooks, etc) uses shared memory. I have a Dell notebook at work, which also has ATI Radeon, same thing.  You can reconfirmed by going into BIOS setup, look for an item which specify shared graphics memory.

---

