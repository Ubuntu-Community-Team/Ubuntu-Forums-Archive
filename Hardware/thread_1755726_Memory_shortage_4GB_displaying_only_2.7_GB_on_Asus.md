---
title: "Memory shortage 4GB displaying only 2.7 GB on Asus 1215n"
date: 2011-05-11
forum: Hardware
---

### Post by junke1990 on 2011-05-11
Hey guys, I've seen a lot of posts online about people having problems with mem and all the posts are solved with enabling PAE but I already have that.

Anyone any clue what to do next?

```

junke@1215N:/proc$ uname -a
Linux 1215N 2.6.35-29-server #51-Ubuntu SMP Fri Apr 15 17:29:46 UTC 2011 x86_64 GNU/Linux

junke@1215N:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2754       1845        909          0         93       1067
-/+ buffers/cache:        684       2070
Swap:            0          0          0

junke@1215N:~$ vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  0      0 930784  95612 1092944    0    0   303    13  151  670 36  4 49 11

junke@1215N:~$ grep --color=always -i PAE /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dts


junke@1215N:~$ sudo dmidecode --type 17 | more
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0017, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0015
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: Manufacturer00
	Serial Number: SerNum00
	Asset Tag: AssetTagNum0
	Part Number: ModulePartNumber00

Handle 0x0019, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0015
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: Manufacturer01
	Serial Number: SerNum01
	Asset Tag: AssetTagNum1


junke@1215N:~$ cat /proc/meminfo
MemTotal:        2820568 kB
MemFree:          927688 kB
Buffers:           95928 kB
Cached:          1095240 kB
SwapCached:            0 kB
Active:           534356 kB
Inactive:        1056632 kB
Active(anon):     406640 kB
Inactive(anon):    84032 kB
Active(file):     127716 kB
Inactive(file):   972600 kB
Unevictable:          16 kB
Mlocked:              16 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:                60 kB
Writeback:             0 kB
AnonPages:        399828 kB
Mapped:           128392 kB
Shmem:             90860 kB
Slab:             176124 kB
SReclaimable:     100012 kB
SUnreclaim:        76112 kB
KernelStack:        2896 kB
PageTables:        21888 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1410284 kB
Committed_AS:    1572148 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      562976 kB
VmallocChunk:   34359140748 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:        8576 kB
DirectMap2M:     2865152 kB


```

---

### Post by junke1990 on 2011-05-11
to make it more clear, I do have 4 GB of ram, 2 x 2GB DDR3 10600 @ 1066Mhz in my Asus eee 1215n but I can only use 2.7 GB.

- My BIOS does see 4 GB, as does dmidecode.
- I am running 64 bit and PAE enabled kernel.
- I used to run @ 2 GB so something has changed.
- I am running a server kernel with a hole lot of mod's enabled as stated above.

Anything else I can try? Could my ION2 (Next/Second Gen) can have anything to do with this? As far as I know, even if your GPU uses shared memory you should see the full mem throughout the system (free -m)

---

### Post by teachop on 2011-05-11
I used to have a 1Gig memory laptop that could be set to reserve a certain quantity of RAM for the shared bus ATI video, it was a BIOS setting.  That video-reserved memory did not appear available to Linux.

---

### Post by junke1990 on 2011-05-11
I can't configure any memory nor GPU settings in the BIOS... The BIOS of the 1215n is really limited...

---

### Post by junke1990 on 2011-05-12
Oke I fixed it! 

I'm now running 8 GB RAM on my Asus eee 1215n.

Update your BIOS, the eee had revision 503 so I updated it to 701 which fixes all your problems!

I had some trouble update the BIOS, the program BUPDATER v 1.16 doesn't run on Hiren's XP live nor Hiren's DOS (whatever version/settings) nor wine nor wineconsole... I had to put win98 on a stick, but that did fix my problem.

The mem i'm using is Corsair.

```

# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0017, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0015
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: Manufacturer00
	Serial Number: SerNum00
	Asset Tag: AssetTagNum0
	Part Number: ModulePartNumber00

Handle 0x0019, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0015
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: Manufacturer01
	Serial Number: SerNum01
	Asset Tag: AssetTagNum1

```

---

### Post by Yellow Pasque on 2011-05-12
Please mark thread solved

---

### Post by Subbeh on 2011-08-22
Thanks junke1990,

I have the same problem. I'm going to try to update my BIOS now. I was wondering though, I was told the 1215n only supports a max of 4gb ram... Did you change something besides the BIOS update to get this to work?

---

### Post by junke1990 on 2011-08-22
Nope I only updated the BIOS to rev 701 but you may endure black screens after installing the 4GB or 8GB, I installed corsair memory and it works like a charm.

---

