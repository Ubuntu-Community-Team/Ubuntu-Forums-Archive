---
title: "SSD write barrier performance on Linux"
date: 2015-05-11
forum: Hardware
---

### Post by Riklaunim on 2015-05-11
I was building a Linux laptop for a friend, with a new SSD and I wanted to compare it with my own. I've made a benchmark [http://openbenchmarking.org/result/1505102-KH-1505100KH56](http://openbenchmarking.org/result/1505102-KH-1505100KH56) and I wondered if it's actually CPU bound, so I used one laptop for both: [http://openbenchmarking.org/result/1505118-KH-1505113KH31](http://openbenchmarking.org/result/1505118-KH-1505113KH31) and in both laptops Crucial MX200 gets around 110 seconds when on SATA connection. It drops to 5 seconds when write barrier gets disabled. I had similar case some time ago with totally different SSD: [http://openbenchmarking.org/result/1404269-PL-1404261PL16](http://openbenchmarking.org/result/1404269-PL-1404261PL16)

Why does Intel SSD has no problem with write barrier performance (where SQLite use it a lot for data consistency promise), while those two other SSDs have noticeable performance "problem" ? Each of them has different controller chipset.

You cant install "phoronix-test-suite" and do such benchmarks too.

---

### Post by dino99 on 2015-05-12
Intel is known to be very active nowadays on the software side, including the kernel's modules and drivers. Might explain a lot of the difference

---

### Post by Riklaunim on 2015-05-12
They use a SandForce chipset with probably some custom firmware. Maybe Phoronix will do a bigger benchmark so the comparison will be more clear.

---

