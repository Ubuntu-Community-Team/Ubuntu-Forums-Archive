---
title: "AMD Processor &quot;model unknown&quot; identification"
date: 2016-12-19
forum: Hardware
---

### Post by marino3 on 2016-12-19
Hello,

I've been given an old used computer. I found this ominous line in the log :

> dmesg | grep microcode
[    1.460712] microcode: AMD CPU family 0xf not supported

The package amd64-microcode (2.20160316.1) is installed. Xenial is up to date. Hereafter are the results on some commands about the CPU.

Is there an issue with the CPU ? What is this "AMD Processor model unknown" ?

Best regards,

MC


> lscpu

Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
Vendor ID:             AuthenticAMD
CPU family:            15
Model:                 127
Model name:            AMD Processor model unknown
Stepping:              1
CPU MHz:               1900.040
BogoMIPS:              3800.08
L1d cache:             64K
L1i cache:             64K
L2 cache:              256K
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm extapic cr8_legacy 3dnowprefetch vmmcall


> sudo dmidecode -t processor

# dmidecode 3.0
Getting SMBIOS data from sysfs.
SMBIOS 2.4 present.

Handle 0x0007, DMI type 4, 35 bytes
Processor Information
    Socket Designation: Socket AM2 
    Type: Central Processor
    Family: 80486
    Manufacturer: AMD
    ID: F1 0F 07 00 FF FB 8B 07
    Signature: Type 0, Family 15, Model 15, Stepping 1
    Version: AMD Processor model unknown
    Voltage: 1.2 V
    External Clock: 200 MHz
    Max Speed: 3000 MHz
    Current Speed: 1900 MHz
    Status: Populated, Enabled
    Upgrade: Socket 939
    L1 Cache Handle: 0x000B
    L2 Cache Handle: 0x000C
    L3 Cache Handle: Not Provided
    Serial Number:  
    Asset Tag:  
    Part Number:  

> cat /proc/cpuinfo

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 127
model name    : AMD Processor model unknown
stepping    : 1
cpu MHz        : 1900.040
cache size    : 256 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm extapic cr8_legacy 3dnowprefetch vmmcall
bugs        : apic_c1e fxsave_leak sysret_ss_attrs
bogomips    : 3800.08
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

---

### Post by mörgæs on 2016-12-19
Strange. I could imagine a situation like this for new hardware but an AM2 socket is around ten years old so all information about the corresponding processor should be stable as well. 

Which release of Buntu did you use for the output?

---

### Post by Yellow Pasque on 2016-12-19
```
CPU family: 15
Model: 127
```
This information matches the Sempron LE-1100. The other characteristics (1.9GHz clock speed, 256KB cache, 1.20V) also match up:
[http://www.cpu-world.com/CPUs/K8/AMD-Sempron%2064%20LE-1100%20-%20SDH1100IAA3DE%20(SDH1100DEBOX).html#cpuid](http://www.cpu-world.com/CPUs/K8/AMD-Sempron%2064%20LE-1100%20-%20SDH1100IAA3DE%20(SDH1100DEBOX).html#cpuid)

```
microcode: AMD CPU family 0xf not supported 
```
If you look at the README file, there are no patches for 0fh family. I would not worry about this message.


```
;******************************************************************************
; The associated microcode container file fixes the errata as documented in
; Revision Guide for AMD Family 10h Processors, order #41322,
; Revision Guide for AMD Family 11h Processors, order #41788,
; Revision Guide for AMD Family 12h Processors, order #44739,
; Revision Guide for AMD Family 14h Models 00h-0Fh Processors, order #47534,
```

---

### Post by marino3 on 2016-12-19
Ok, thanks a lot Temüjin. The machine is old, but will do (mainly LibreOffice and mail).

Best regards

MC

---

