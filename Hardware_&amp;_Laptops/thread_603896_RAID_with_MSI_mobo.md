---
title: "RAID with MSI mobo"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by Weidbrewer on 2007-11-05
Silly noob question:   Looking to set up a three drive RAID deal with the below motherboard.   Will I need to get a raid card, or will I be able to do it with just the motherboard?

Hardware:  MSI K9N Neo-F AM2 NVIDIA nForce 550 MCP ATX AMD Motherboard

Either way, is there a good tutorial out there I could follow?

Thanks in advance for the help.

---

### Post by psusi on 2007-11-05
You should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by Weidbrewer on 2007-11-05
Thanks for the pointer.

Reading through that, I am better able to frame my question.   (Isn't that always the case?   The more you learn, it's simply the better you can ask a question.)

I'm not looking to set it up to duel boot/access between Widnows and Linux.   What i am looking to do is set up a RAID-5 system for data back-up.   That tutorial looks to say that it can't be done at this time.   Is there are hardware solution to this, or is software the only way to go about this under Ubuntu?

---

### Post by psusi on 2007-11-06
Yea, the hardware solution is to buy an expensive hardware raid card.  The software solution is to use conventional linux software raid and disregard the fake raid functionality on your motherboard.

---

