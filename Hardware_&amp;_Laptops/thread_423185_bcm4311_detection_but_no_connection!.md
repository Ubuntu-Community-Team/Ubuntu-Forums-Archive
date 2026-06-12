---
title: "bcm4311 detection but no connection!"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by noahtron on 2007-04-25
hello,

i am a linux newbie, and i'm trying to get the *famous* broadcom bcm4311 wireless card to work on my lenovo under feisty.
i followed the instructions on [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29), and everything seemed to go off without a hitch. the result is i can **detect** wireless access points in my area (ubuntu in roaming mode), but i cannot **connect** to any of them! it's quite frustrating.
the access point where i live is a linksys 802.11g wireless router.

any ideas?

---

### Post by bdogg64 on 2007-04-25
are you sure you blacklisted the old bcm43xx driver?

---

### Post by noahtron on 2007-04-26
yup bcm43xx is blacklisted!

update:
so i can connect now. don't know why my compy changed its mind... but in order to connect i have to close the lid (hibernate) and then reopen it; at which point it connects with no trouble at all! wierd, no?

any thoughts?

---

