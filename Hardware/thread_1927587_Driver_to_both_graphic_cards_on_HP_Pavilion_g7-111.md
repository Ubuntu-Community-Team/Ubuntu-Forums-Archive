---
title: "Driver to both graphic cards on HP Pavilion g7-1110so"
date: 2012-02-18
forum: Hardware
---

### Post by KingOfTheNothing on 2012-02-18
Hi!

I have laptop HP Pavilion g7-1110so and Ubuntu 64 11.10. 

There are two graphic cards installed see detailes below. The major one does not function anyone that has solved this issue? What driver is needed?

Thanks!

XXXXXXX:~$ lspci -nn | grep VGA
00:02.0  VGA compatible controller [0300]: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] [1002:6760]

---

### Post by Mark Phelps on 2012-02-20
This is known as Hybrid Graphics and is not well supported in Linux.  See the info below:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by RayVad on 2012-02-25
Hi KingOfTheNothing,

Did you got this working?
Having also a HP G7 pavilion 1270sd, but can't even start the laptop without the nomodeset option.
Using Mint 12 here.


lspci -nn|grep VGA:
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] [1002:6760]


Ray

---

