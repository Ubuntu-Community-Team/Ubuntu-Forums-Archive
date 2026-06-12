---
title: "Need help with Raid."
date: 2008-08-05
forum: General Help
---

### Post by Thyssenkrupp on 2008-08-05
So, if ive got it right, its where you have to HDD's, exactly the same make and size etc. and you make it so that the computer sees it as one HDD, how do i do this??


Jak

---

### Post by Paradoxalley on 2008-08-05
If you don't have hardware support for RAID in your computer (RAID card or on-chip RAID) then you should look at LVM and MD (software-based RAID). The level of RAID you are talking about is RAID-1 where you have mirrored data between two physical drives and effectively keep two copied of your data. You can read more about setting it up on an existing system here:
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
or during installation here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Taxman415a on 2008-08-05
Actually if you don't have fakeraid, you don't want that installation method. The Wiki pages really need to cross link and coordinate better. Searching for raid also brought up this page:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
which seemed easier to understand.
Also Jak, you may want to read [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID) for background.

---

