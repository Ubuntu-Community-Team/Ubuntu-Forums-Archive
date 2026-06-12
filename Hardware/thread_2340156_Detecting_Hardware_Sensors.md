---
title: "Detecting Hardware Sensors"
date: 2016-10-16
forum: Hardware
---

### Post by SageOfSmeg on 2016-10-16
I have an old (circa. 1999) desktop machine running dual-boot with Lubuntu 14.04.5 and Windows98.
It is a PC-Chips Motherboard M726, PC100 768MB RAM, Pentium II 350MHz.
 
Despite installing psensor and mpack I am unable to detect full  sensor information. Psensor was only able to monitor CPU usage, it was  not detecting CPU or MB temperatures, nor any fan speeds. All internal cables are correctly connected.
 
From within Windows98 I can use an old utility called MBProbe, which works fine and can detect the hardware sensors without any problem, so I know that the sensors are technically functioning.
 
I have tried running MBProbe under Lubuntu via wine but it won’t run because it is missing the giveio.sys file, which sadly doesn’t seem to be available any more, or at least I can’t find a trustworthy download.
 
From within Windows98 I can get the following MBProbe sensor info:
CPU...
- Name: GenunineIntel Pentium II .20u
- Details: Family 6 Model 5 Stepping 2, 2.00v
System...
- SMBus: ALiM1543C port 440h
- Sensors: GL520SM rev 0h SMBus address 2Dh
 
Can anybody advise suitable sensor software?
Thanks

---

