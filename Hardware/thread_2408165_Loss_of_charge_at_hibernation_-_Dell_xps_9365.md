---
title: "Loss of charge at hibernation - Dell xps 9365"
date: 2018-12-14
forum: Hardware
---

### Post by mfox on 2018-12-14
I recently purchased a Dell xps 13 2 in 1 (2018 edition) with the i5-8500Y processor. I installed Ubuntu 18.10 on it, and it is working perfectly except for excess battery drain at sleep. I am replacing a 3 year old Dell xps 13 (9343), also running Ubuntu 18.10 and it doesn't have this problem. I have swap partitions on both.

The difference is extreme; in the new laptop I seem to lose 5% power per hour, whereas the old loses only 5-10% per day. Since I frequently leave my laptop in sleep mode and don't come back to it in a day, the new laptop has no charge left after a day, whereas the old one only needs to be recharged every 4-5 days. In both laptops, the sleep mode enabled is s2idle, not deep. When I temporarily change the 2 in 1 to deep mode:
```
sudo journalctl | grep "PM: suspend" | tail -2
```
the laptop doesn't wake up and has to be rebooted. I'm wondering if there is a solution for this problem.

---

