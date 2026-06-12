---
title: "dmidecode command"
date: 2011-03-23
forum: Hardware
---

### Post by newbuntuxx on 2011-03-23
Hello,

I bought a Kingston Dual 2G kit (KHX8500D2K2/4G	4GB DDR2 1066MHz Non-ECC CL5(kit of 2 – 2GB)) [Data Sheet]("http://www.valueram.com/datasheets/KHX8500D2K2_4G.pdf")

After installing the two memory modules, I ran "dmidecode" to check the speed that the memory modules are running at, and i got the following:


```
Memory Device
	Array Handle: 0x002E
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 333 MHz (3.0 ns)
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0

Handle 0x0032, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002E
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 333 MHz (3.0 ns)
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
```

Now, the sticks should operate at a maximum of 1066 Mhz, but dmidecode shows that they are operating at 333 Mhz. 

Can anyone please explain why this is happening? Perhaps I am misunderstanding something here?

---

### Post by Yellow Pasque on 2011-03-23
First off, DDR means Double Data Rate, so it's running at DDR2-667.
Next, you have to manually set the voltage and latencies in your BIOS. You also have to make sure you have the base clock and multiplier set correctly.
If you're still confused, more info on your system would be appropriate (mobo and CPU)

---

### Post by newbuntuxx on 2011-03-24
Hey, 

Thanks for the reply. I think I know what you are saying, but I certainly wouldn't mind you walk me through it.

Motherboard:


```
Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASUSTeK Computer INC.
        Product Name: P5GC-MX/1333
        Version: Rev x.xx
        Serial Number: MB-1234567890
        Asset Tag: To Be Filled By O.E.M.
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: To Be Filled By O.E.M.
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0

```

CPU:
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
stepping	: 11
cpu MHz		: 2664.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 4257.34
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
stepping	: 11
cpu MHz		: 2664.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 4257.59
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

---

### Post by Yellow Pasque on 2011-03-24
Every mobo's BIOS is different, so it's not as easy as copy/pasting commands. Are you trying to overclock?

---

### Post by newbuntuxx on 2011-03-24
Well, what I am trying to do is simply take advantage of my 1066 bus speed. If that means I need to over clock my cpu, then so be it.

Do you have any suggestions? Or general guide lines that I need to follow? Things that I should do/not do?

---

### Post by Yellow Pasque on 2011-03-24
Well, there's a RAM speed selection in the BIOS, which is its cryptic way of letting you set a divider, which is what you want to do to run your memory at that speed.

---

### Post by newbuntuxx on 2011-03-24
So, here is what I have in my bios under advanced:

Configure system frequency/voltage:

AI over clocking: [manual/auto]

If I set it to manual, then I get the following options:

1. CPU Frequency [333] (Acceptable values are: [100-450])

2. DRAM Frequency [AUTO] (If I click on Auto, I see the following: DDR2 500Mhz, DDR2 666MHZ, DDR2 833MHZ)Now these values will change depending on what I choose for number 1.

3. PCI Frequency (I don't think its relevant)

---

### Post by Yellow Pasque on 2011-03-24
I think you should post on Hard|OCP or something, as they're better at this kind of thing.
Personally, I would select DDR2-667 to lock the memory to the base clock with no divider, and try to get the base clock to 400MHz (which would run the memory @ DDR-800). Of course, this means that your CPU will run at 3.2GHz, so a voltage bump may be needed. Even if the RAM isn't running at DDR2-1066, it may still be worth the premium if you can tighten the timings.

---

