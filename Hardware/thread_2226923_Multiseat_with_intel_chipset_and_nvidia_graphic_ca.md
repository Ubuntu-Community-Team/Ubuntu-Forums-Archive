---
title: "Multiseat with intel chipset and nvidia graphic card"
date: 2014-05-29
forum: Hardware
---

### Post by ypetremann on 2014-05-29
Hello, I would like to configure my home computer to have Multiseat capability, it contain a intel chipset on the motherboard and independent nvidia graphic card.

I would like to have the intel chipset for a office and internet session for my familly and the nvidia card for gaming and everything else at the same time.

Before I activated the Intel chipset, Ubuntu was correctly using my nvidia card. After that, my bios boot on the nvidia card but grub appear on the intel card. On Ubuntu only the screens connected to the motherboard are detected and nothing about nvidia else that :

```
user@computer:~$ lspci -vnn| grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104 [GeForce GTX 760] [10de:1187] (rev a1) (prog-if 00 [VGA controller])
```

I would like to detect nvidia screens because I would like to use a script like becephal to configure multiseat, I think that Xorg is ignoring Nvidia because it has the intel chipset. How could I make both working at the same time ?

---

