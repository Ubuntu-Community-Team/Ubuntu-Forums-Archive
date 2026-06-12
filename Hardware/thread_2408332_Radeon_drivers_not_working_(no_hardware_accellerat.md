---
title: "Radeon drivers not working (no hardware accelleration) showing LLVMpipe"
date: 2018-12-17
forum: Hardware
---

### Post by waninstall on 2018-12-17
My system shows: 

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Sumo [Radeon HD 6480G] [1002:9649]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760]

This might mean I have a hybrid integrated/dedicated GPU? The laptop is Lenovo edge e425 from 2012. 

However it says I'm on LLVMpipe, and things are running really slowly. How do I use AMD drivers?

---

### Post by him610 on 2018-12-17
How about showing, between the code tags, the results of ```
inxi -SMCG
```

---

