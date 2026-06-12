---
title: "Problem with bcm4312 in ubuntu 10.04!!!"
date: 2010-06-19
forum: Hardware
---

### Post by Dlambert on 2010-06-19
Hello, i have an interesting problem and any suggestions would be helpful. I have an inpiron 1545 with 2gigs of ram, 160GB western digital hard drive, Intel gm45, bcm4312 wireless card. I installed the bcm43-fwcutter and now my wireless works, but every few keystrokes my mouse and keyboard freeze, but as soon as i remove/disable wirless it works fine. What is causing this, and how do i fix it?



              Thanks

---

### Post by Dlambert on 2010-06-19
nvm, fixed it!

---

### Post by ravindu_w on 2010-07-10
I have an hp mini 2133 with ubuntu 10.04. i installed the dependencies and then the bcmwl-kernal-source and it got installed without any errors. but when check for drvers theres nothing in the hardware driver window. I dont have a wired connection. pls help.

---

### Post by Dlambert on 2010-12-03
You shouldn't need any more drivers...Its the BCWL STA driver or something like that.

---

### Post by sbrbot on 2010-12-20
HP Mini 2133 does have BCM4312 (14e4:4315) wireless card and it can work with both, STA or B43 drivers. Broadcom STA driver does not support packet injection.

Moreover 2133 does have low power wireless card BCM4312 (LP-PHY) and Ubuntu 10.10 (not earlier versions) has package **firmware-b43-lpphy-installer** with wireless card firmware v4.174.64.19-4 (sometimes referred as v4.178.10.4 as well) which supports packet injection!

---

### Post by Dlambert on 2010-12-31
Good to know.
:KS:KS:KS:KS:KS

---

