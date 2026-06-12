---
title: "Hardware (Intel CPU) Error - MCELog Output"
date: 2011-09-06
forum: Hardware
---

### Post by daxumaming on 2011-09-06
Hi guys
I would just like to verify that the output is indeed a CPU problem. And if there's anything else I could do to solve the random shutdown besides replacing my CPU.

I have an Asustek P5KPL-AM EPU mobo with Intel Core 2 Duo E7500 running at 2.93GHz (as per lshw) and 2pcs 2GB DDR2 800MHz running Ubuntu Natty 64-bit.

Thanks

```

HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 0
CPU 0 BANK 0
TIME 1315087801 Sun Sep  4 06:10:01 2011
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
failure that caused IERR
STATUS f200084000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0
CPUID Vendor Intel Family 6 Model 23
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 1
CPU 0 BANK 5
TIME 1315087801 Sun Sep  4 06:10:01 2011
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE driven
STATUS f200001014000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0
CPUID Vendor Intel Family 6 Model 23
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 2
CPU 1 BANK 5
TIME 1315087801 Sun Sep  4 06:10:01 2011
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven MCE is observed
STATUS f200001030000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0
CPUID Vendor Intel Family 6 Model 23

```

---

### Post by zorkerz on 2012-06-25
Hey daxumaming,
My mcelog looks very similar to your post. [See here]("http://ubuntuforums.org/showthread.php?p=12053527#post12053527"). Did you ever find out more about this?

---

### Post by Redblade20XX on 2012-06-25
> **zorkerz said:**
> Hey daxumaming,
My mcelog looks very similar to your post. [See here]("http://ubuntuforums.org/showthread.php?p=12053527#post12053527"). Did you ever find out more about this?

 From the logs given by OP, it seems as if the CPU is damaged and needs to be replaced. It looks as if the processor cannot clear the contents of a register.  -Red

---

### Post by zorkerz on 2012-06-25
Here is my mcelog: mcelog: ```
failed to prefill DIMM database from DMI data
mcelog: mcelog read: No such device
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 0 
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
failure that caused IERR
STATUS f200084000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 1
CPU 0 BANK 5 
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE driven
STATUS f200001014000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 2
CPU 1 BANK 5 
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven MCE is observed
STATUS f200001030000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
mcelog: failed to prefill DIMM database from DMI data
mcelog: mcelog read: No such device
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 0 
TIME 1340646534 Mon Jun 25 13:48:54 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
failure that caused IERR
STATUS f200084000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 1
CPU 0 BANK 5 
TIME 1340646534 Mon Jun 25 13:48:54 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE driven
STATUS f200001014000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 2
CPU 1 BANK 5 
TIME 1340646534 Mon Jun 25 13:48:54 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven MCE is observed
STATUS f200001030000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
```

Does it look like the same problem as the OP? 
If so what part of the mcelog points to it or is it better to look somewhere else?

I am financially unable to replace the cpu on this system for considerable amount of time. Is there anything I can do to try and avoid system freezes in the interim? 

Thanks

---

### Post by Redblade20XX on 2012-06-25
> **zorkerz said:**
> Here is my mcelog: mcelog: ```
failed to prefill DIMM database from DMI data
mcelog: mcelog read: No such device
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 0 
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
failure that caused IERR
STATUS f200084000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 1
CPU 0 BANK 5 
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE driven
STATUS f200001014000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 2
CPU 1 BANK 5 
TIME 1340634209 Mon Jun 25 10:23:29 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven MCE is observed
STATUS f200001030000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
mcelog: failed to prefill DIMM database from DMI data
mcelog: mcelog read: No such device
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 0 
TIME 1340646534 Mon Jun 25 13:48:54 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
failure that caused IERR
STATUS f200084000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 1
CPU 0 BANK 5 
TIME 1340646534 Mon Jun 25 13:48:54 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE driven
STATUS f200001014000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
Hardware event. This is not a software error.
MCE 2
CPU 1 BANK 5 
TIME 1340646534 Mon Jun 25 13:48:54 2012
MCG status:
MCi status:
Error overflow
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven MCE is observed
STATUS f200001030000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 15
```Does it look like the same problem as the OP? 
If so what part of the mcelog points to it or is it better to look somewhere else?

I am financially unable to replace the cpu on this system for considerable amount of time. Is there anything I can do to try and avoid system freezes in the interim? 

Thanks

Does the computer randomly freezes or does it after a set time? If it's random, try cooling down the cpu ( clean the fans inside, set the fans on max, etc.) because it could be related to heat. This is also a temp fix if it works, though.
You should also try asking this question on your cpu's manufacturer forum.

-Red

---

### Post by zorkerz on 2012-06-25
It just freezes randomly. I've been trying to monitor the CPU core temperatures and they seem to stay within acceptable ranges. I replaced the heatsink/fan unite a few months ago because the fan was clearly starting to die. The freezing seemed to be less frequent for a while. I just order some more thermal past, in case I did a poor job putting that on. But all in all I think the temperatures are ok. 

I'll have to move over to the intel forum see if anyone can help there.

thanks red

---

### Post by daxumaming on 2012-06-26
thanks guys, already replaced the CPU. though I kept on wondering what made my CPU fail.

---

