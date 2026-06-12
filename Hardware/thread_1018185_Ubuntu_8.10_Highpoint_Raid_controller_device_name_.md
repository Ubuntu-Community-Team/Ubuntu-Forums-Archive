---
title: "Ubuntu 8.10 Highpoint Raid controller device name changes"
date: 2008-12-21
forum: Hardware
---

### Post by jcustenborder on 2008-12-21
Hi All, 

I'm running into an issue with my 8.10 box using a Highpoint raid controller. When I installed the box the raid controller was found as /dev/sdb. I have a regular hard drive that ubuntu is installed to as /dev/sda. Everything worked ok for a while. Now I am having issues where the highpoint controller is showing up as /dev/sda* which causes the box to kernel panic on boot. How can I ensure that my onboard sata controllers are loaded before my raid controller?  The raid controller is a Highpoint 3522. 

J

---

