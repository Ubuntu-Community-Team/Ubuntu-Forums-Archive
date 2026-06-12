---
title: "Device Manager"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by Elite195 on 2006-10-26
Hi everybody,

i have a AMD Athlon XP2600+ processor. When i look at cpuinfo at the terminal, the cpu data is displayed correctly. But when i take a look at my processor in the Device Manager the vendor etc. of the processor is unknown.
Is this a bug, or a serious problem?

Thank´s.

---

### Post by magicfab on 2006-10-27
an you upload a screenshot ?

---

### Post by ironfistchamp on 2006-10-31
I have the same prob in Dapper and Edgy. I will try and get a screenshot but basically dmesg shows the correct name and other information about my CPU and other hardware but the Device Manager says unknown next to lots of the labels for much of my hardware. Example

> 
Processor

Vendor: Unknown
Device: Unknown

Status: Status
Bus Type: Unknown

Device Type: processor
Capabilities: processor


I have an AMD X2 4200+ just installed today and dmesg says this

> 
dstamp@dubuntu:~$ dmesg | grep AMD
[17179570.448000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
[17179570.540000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01

--snip--

[17179611.872000] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.60.2)


Any ideas anyone?

Thanks

Ironfistchamp

---

