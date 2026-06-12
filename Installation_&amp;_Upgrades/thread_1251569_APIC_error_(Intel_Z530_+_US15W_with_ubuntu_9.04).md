---
title: "APIC error (Intel Z530 + US15W with ubuntu 9.04)"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by RobertF on 2009-08-27
We use newest ubuntu 9.04 with Intel Z530 + US15W; however, the system shows APIC errors as below.
 
dmesg.4.gz:[ 4.189022] APIC error on CPU0: 00(80)
dmesg.4.gz:[ 4.252030] APIC error on CPU0: 80(80)
dmesg.4.gz:[ 4.437316] APIC error on CPU1: 00(40)
 
Does any one have idea for them?
 
It happens thousands and thousands of times; slows down the system; and causes the network to drop, so I disabled apic in the kernel and (for now) it seems better. However, the performance drops down way much.
 
Could any kernel expert help this issue?

---

