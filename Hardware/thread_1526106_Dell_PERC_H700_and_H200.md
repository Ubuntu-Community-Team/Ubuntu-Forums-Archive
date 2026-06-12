---
title: "Dell PERC H700 and H200"
date: 2010-07-07
forum: Hardware
---

### Post by sugar2 on 2010-07-07
Dell PowerEdge R310
RAID Card H700
Ubuntu 10.04 Server Ed. i386

Hi, do somebody knows if Dell H700 PERC hardware works in latest Ubuntu Server 10.04? 
 I ask this because I got a Dell Server with Software PERC S300 and I realized its a Software RAID... and I want a Hardware one...

thanks in advance!!

Aldo

---

### Post by mfsandoval on 2010-07-09
The PERC H700 as well as the PERC H200 use the same driver that is on the Ubuntu 10.04 --> MPT2SAS.  This driver is on the latest offering of Ubuntu.  Before loading the OS using the H700 as your RAID controller, disable the PERC S300 via the BIOS settings.
 
Regards,
 
Martin Sandoval

---

### Post by sugar2 on 2010-07-09
thanks a lot for the information!!

Aldo

---

### Post by furo83 on 2011-01-11
> **mfsandoval said:**
> The PERC H700 as well as the PERC H200 use the same driver that is on the Ubuntu 10.04 --> MPT2SAS.  This driver is on the latest offering of Ubuntu.  Before loading the OS using the H700 as your RAID controller, disable the PERC S300 via the BIOS settings.
 
Regards,
 
Martin Sandoval

Sorry but i have the same problem...

Where i can disable the PERC S300???

thanks
Claudio

---

### Post by ZTiger on 2011-05-03
> **furo83 said:**
> Sorry but i have the same problem...

Where i can disable the PERC S300???

thanks
Claudio

You'll want to remove the S300 card from the motherboard. The S300 is a software raid and most Linux distros have problems with it. Best bet is to use the Perc 6/i, H200 or H700 all of which should work with 10.04 and 10.10. If memory servers they use the mpt2sas drivers that are in the 2.6.30 kernel so it should work with any Ubuntu after 9.04

---

