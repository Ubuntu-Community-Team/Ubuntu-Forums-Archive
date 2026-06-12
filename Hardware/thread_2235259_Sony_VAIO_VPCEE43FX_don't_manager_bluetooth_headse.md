---
title: "Sony VAIO VPCEE43FX don't manager bluetooth headset service in Ubuntu 12 +"
date: 2014-07-19
forum: Hardware
---

### Post by tylervortexbr on 2014-07-19
Hello my friends,

My problem is a **Sony Vaio VPCEE43FX** don't **find/connect/wizard** **bluetooth** headset service in Ubuntu 12.* or 14.*
My Headset bluetooth is "BOAS", Made In China, which usually runs on android smartphone.

I run command in terminal


$ hcitool dev

```
Devices:

```


$ rfkill list

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```



lsmod | grep bluetooth

```
bluetooth             391196  10 bnep,rfcomm


```


Please help me in this problem. :(

---

