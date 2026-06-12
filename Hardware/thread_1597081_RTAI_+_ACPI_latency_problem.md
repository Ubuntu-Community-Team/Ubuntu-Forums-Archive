---
title: "RTAI + ACPI latency problem"
date: 2010-10-14
forum: Hardware
---

### Post by ryecomp on 2010-10-14
H/W : Intel 1.6GHz, BioStar U8548
S/W : Ubuntu 8.04 + RTAI + EMC2 (CNC controller) 

In configuring CNC controller system, latency-test must be run
to find maximum jitter of the system. It counts about 17,000 ns 
for few minutes, then it suddenly rise to 260,000 ns. It is impossible
to control CNC with such large jitter. 

In tracing this problem, I found that Award BIOS setting 
"Delay Prior to Thermal" is firmly engaged in making a problem.
When I set this setting to 4 minutes, it makes large jitter periodically 
with exact 4min 15sec period. When I changed this setting to 8 minutes,
its jitter is 8min 15sec period. 

But, there is no option to disable this BIOS setting. 

I heard that ACPI enabled OS can take over the ACPI function of the
BIOS (which may include this "thermal" setting), but RTAI tuned 
kernel don't include ACPI modules. 

Is there any solution to this problem ? If I recompile kernel with 
RTAI with ACPI processor module enabled, would it be a another 
problem maker ?

---

