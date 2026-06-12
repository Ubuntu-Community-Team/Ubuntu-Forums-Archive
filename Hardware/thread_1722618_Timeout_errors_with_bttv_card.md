---
title: "Timeout errors with bttv card"
date: 2011-04-06
forum: Hardware
---

### Post by kladizkov on 2011-04-06
Hi,

I'm trying to setup my Pinnacle PCTV card in my ubuntu. It doesn't tune the frequencies correctly while running tvtime-scanner. I get these messages in my /var/log/messages file. How can I fix it and configure the channels properly.
 
```

Apr  5 18:14:43 sunshine kernel: [24568.820014] bttv0: timeout: drop=25 irq=557/557, risc=37b6803c, bits: HSYNC OFLOW
Apr  5 18:15:35 sunshine kernel: [24621.280016] bttv0: timeout: drop=320 irq=4054/4054, risc=37b6803c, bits: HSYNC OFLOW
Apr  5 18:16:41 sunshine kernel: [24687.260017] bttv0: timeout: drop=27 irq=239/239, risc=9bfe003c, bits: HSYNC OFLOW FBUS FDSR
Apr  5 18:17:02 sunshine kernel: [24707.701265] bttv0: timeout: drop=158 irq=1741/1741, risc=9a4c8024, bits: HSYNC OFLOW FDSR
Apr  5 18:17:08 sunshine kernel: [24713.540016] bttv0: timeout: drop=189 irq=2163/2163, risc=9bfe003c, bits: HSYNC OFLOW
Apr  5 18:23:33 sunshine kernel: [25099.070018] bttv0: timeout: drop=93 irq=1048/1048, risc=98fa0024, bits: HSYNC OFLOW FDSR
Apr  5 18:24:32 sunshine kernel: [25158.230017] bttv0: timeout: drop=461 irq=5371/5371, risc=7c01303c, bits: HSYNC OFLOW
Apr  5 18:24:36 sunshine kernel: [25161.490016] bttv0: timeout: drop=479 irq=5606/5606, risc=993e1044, bits: HSYNC OFLOW FDSR
Apr  5 18:36:04 sunshine kernel: [  106.300131] bttv0: timeout: drop=67 irq=1541/1543, risc=83a3311c, bits: HSYNC OFLOW FDSR

```

---

