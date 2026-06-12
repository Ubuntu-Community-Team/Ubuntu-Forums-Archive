---
title: "Any problems with swap space half size of memory?"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by mattengland on 2007-06-10
On my Ubuntu 7.04 Thinkpad T41, I set my swap space to half the size of my memory (physical memory = 2GB, swap parition size = 1GB).

Will this present any problems, particularly with hibernate?

---

### Post by ofir_k on 2007-06-10
Simply add more swap!
[https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0](https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0)

---

### Post by Outrunner on 2007-06-10
> **ofir_k said:**
> Simply add more swap!
[https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0](https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0)

How useless. He will never need that much(except in special situations). I have 1GB of RAM and 300 swap, and I don't think I'll ever use that much...

---

### Post by mattengland on 2007-06-10
Hmmm...converting my swap parition to a file (instead of a fixed paritition) gets a more storage space flexibility for my storage-constrained laptop...assuming this works.

Can anyone verify that their swap-as-a-file-and-not-as-a-parition configuration is working?

---

### Post by CrispyFried on 2007-06-10
my compaq m2010 notebook hibernates fine with a 768 meg swap and one gig of ram. unless you hibernate with some monster app running you can probably get away with it. Id rather not give it anymore as I only have a 40 gig drive in it.

dunno about the swap-as-a-file bit.

---

### Post by mattengland on 2007-06-10
> **CrispyFried said:**
> my compaq m2010 notebook hibernates fine with a 768 meg swap and one gig of ram. unless you hibernate with some monster app running you can probably get away with it. Id rather not give it anymore as I only have a 40 gig drive in it.

Thanks for the info.  This quote implies that the hibernation function saves the physical memory contents into the actual swap space.  Is this truly the case?  eg, last I knew Windows saved hibernate-memory contents in a file on the filesystem (which may be what happens per the swap-as-a-file-conifg stuff mentioned above).

Can anyone authoritatively comment on this?

---

### Post by 444 on 2007-06-10
Last I checked Linux hibernates to a swap *partition* only. It has to be as big as the memory you're using, eg if you only use a little of your ram you can get away with smaller sizes.

If you're not hibernating then I'd stick with a 200m swap file since I have more than enough ram. Keeping some so you know when you run out of memory via hd noise instead of your app suddenly being forced closed cuz of lack of ram.

---

