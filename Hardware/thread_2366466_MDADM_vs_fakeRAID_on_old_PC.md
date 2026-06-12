---
title: "MDADM vs fakeRAID on old PC"
date: 2017-07-18
forum: Hardware
---

### Post by idevoid on 2017-07-18
Hi, I have a local media server which runs Lubuntu 16. It's an old PC, Intel Pentium 4. and I run out of space in the storage I found that linux has MDADM to create RAID Array.. Well, I'm thinking that software is too hard for my Intel Pentium 4 to handle.. so, i was searching [cheap RAID hardware]("https://www.newegg.com/Product/Product.aspx?Item=N82E16816124024&Tpk=N82E16816124024").. but, some people on internet said cheap RAID hardware isn't a great idea.. and a [wiki]("https://help.ubuntu.com/community/FakeRaidHowto") says linux software raid is recommended over fakeRAID/cheap RAID hardware.. and the biggest problem is i don't know if that cheap RAID hardware would work or not on my local media server.. what's your opinion?
i still have to buy a card whatever the option is.. and there is 3 options:
1. buy SATA expansion card for MDADM to create RAID
2. buy fakeRAID / cheap RAID hardware to create RAID
3. buy SATA expansion card to add partition and NOT creating RAID (only if creating RAID on my server is a bad idea)
Note: i already have unused HDDs, that's why i won't buy new HDD
Thank you

---

### Post by TheFu on 2017-07-18
Welcome to the forums.

Don't use FakeRAID - ever.

Do you realize that for $120 or so, you could have a modern computer easily capable of all you ask, provided you can reuse the extra parts like the PSU, case, HDDs, mouse, keyboard, etc?  You would only need a $50 CPU, $50 Motherboard and $20 in RAM to achieve this.  3 yrs ago, I did it - with an intel G3258 CPU for $49 and a Gigabyte $49 motherboard and $16 in DDR3 RAM.  There should be a newer, faster, generation CPU now.

The only issue I can see is that new MBs are all SATA, not IDE, so if your P4 MB is mostly/all IDE, then you won't be able to use the old HDDs.

---

