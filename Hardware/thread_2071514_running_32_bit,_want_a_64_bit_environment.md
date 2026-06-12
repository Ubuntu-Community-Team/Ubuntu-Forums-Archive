---
title: "running 32 bit, want a 64 bit environment"
date: 2012-10-15
forum: Hardware
---

### Post by unibroker on 2012-10-15
I am currently running 12.04 on a 6 year old computer and couldn't be happier.  I would like to build Android's Jelly Bean from source but that takes a 64 bit platform.  Is my only option to buy a separate tower?

---

### Post by oldfred on 2012-10-15
My computer is about 6 years old and has Intel Core Duo so it is 64 bit. I have run 64bit since 9.10 on it.

So what processor do you have and how much RAM. You need a 64 bit processor and 3GB of RAM as the minimums.

[https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html)

What do these show:
lscpu
cat /proc/cpuinfo
cat /proc/meminfo

---

### Post by Cheesemill on 2012-10-15
Copy and paste this into a terminal:
```
grep -q "^flags.*\blm\b" /proc/cpuinfo && echo "Yes you have a 64 bit cpu" || echo "No 64 bit for you"
```(Blatantly stolen from a post by wojox yesterday :))

---

### Post by unibroker on 2012-10-15
> **oldfred said:**
> My computer is about 6 years old and has Intel Core Duo so it is 64 bit. I have run 64bit since 9.10 on it.

So what processor do you have and how much RAM. You need a 64 bit processor and 3GB of RAM as the minimums.

[https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html)

What do these show:
lscpu
cat /proc/cpuinfo
cat /proc/meminfo


lscpu:

```
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              6
CPU MHz:               1600.000
BogoMIPS:              3733.76
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              2048K

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping    : 6
microcode    : 0x44
cpu MHz        : 1600.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow
bogomips    : 3733.13
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```

cat /proc/cpuinfo:
```
processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping    : 6
microcode    : 0x44
cpu MHz        : 1600.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow
bogomips    : 3733.76
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```

cat /proc/meminfo:
```

MemTotal:        1995028 kB
MemFree:          278604 kB
Buffers:           84568 kB
Cached:           704980 kB
SwapCached:            0 kB
Active:           773072 kB
Inactive:         825608 kB
Active(anon):     514128 kB
Inactive(anon):   305208 kB
Active(file):     258944 kB
Inactive(file):   520400 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:       1186692 kB
HighFree:          15388 kB
LowTotal:         808336 kB
LowFree:          263216 kB
SwapTotal:       2093052 kB
SwapFree:        2093028 kB
Dirty:                16 kB
Writeback:             0 kB
AnonPages:        809172 kB
Mapped:           136972 kB
Shmem:             10204 kB
Slab:              66816 kB
SReclaimable:      48248 kB
SUnreclaim:        18568 kB
KernelStack:        3536 kB
PageTables:        11916 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3090564 kB
Committed_AS:    3456868 kB
VmallocTotal:     122880 kB
VmallocUsed:       50800 kB
VmallocChunk:      61732 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       98296 kB
DirectMap4M:      811008 kB
```


I saw the second line of output ("CPU op-mode(s): 32-bit, 64-bit") from the first piece of data you asked for and thought "Fred's going to blacklist me!".  Everything I've read online led me to believe that my computer was not 64 bit capable.

---

### Post by wojox on 2012-10-15
> **Cheesemill said:**
> Copy and paste this into a terminal:
```
grep -q "^flags.*\blm\b" /proc/cpuinfo && echo "Yes you have a 64 bit cpu" || echo "No 64 bit for you"
```(Blatantly stolen from a post by wojox yesterday :))

:p I stole it from the Arch wiki.

---

### Post by Cheesemill on 2012-10-15
@unibroker

Yes, you have a 64-bit machine.

There is no way of upgrading from a 32-bit to a 64-bit installation though, you will have to do a clean installation.

---

### Post by unibroker on 2012-10-15
> **Cheesemill said:**
> @unibroker

Yes, you have a 64-bit machine.

There is no way of upgrading from a 32-bit to a 64-bit installation though, you will have to do a clean installation.

Thanks.  With tail between legs, I just edited my results post.  

I'll have to upgrade my RAM as well.  From what little I've read on the subject will my resources currently flourishing under a 32 bit system still perform under a 64 bit one?

---

### Post by oldfred on 2012-10-15
I also have 64bit on my laptop which also is a core duo but low spec and only 1.5GB of RAM. It really does not have enough RAM for 64 bit but I run 64 bit just to have same version as my Desktop. Only occasionally does screen go grey (swapping?) as I may have too much going on at once. But on laptop I try not to open too many apps at once.

It looks like you have 2GB of RAM, upgrade would be good, but you should be able to run 64 bit as is.

You will need to backup all of /home if not a separate partition and export a list of installed applications if you want to easily reinstall. I reinstall all the time, but a recent poster did have issue reinstalling when changing from 32 to 64 bit. Not sure if bug, or something else.

 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by typhoon_tip on 2012-10-15
To see if you *can* upgrade RAM, and what type to buy, please post the output of this command:

```
sudo dmidecode --type memory
```

:)

---

### Post by unibroker on 2012-10-15
> **typhoon_tip said:**
> To see if you *can* upgrade RAM, and what type to buy, please post the output of this command:

```
sudo dmidecode --type memory
```

:)

```
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0006, DMI type 5, 24 bytes
Memory Controller Information
	Error Detecting Method: 8-bit Parity
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 4096 MB
	Supported Speeds:
		Other
	Supported Memory Types:
		Other
	Memory Module Voltage: 5.0 V
	Associated Memory Slots: 4
		0x0007
		0x0008
		0x0009
		0x000A
	Enabled Error Correcting Capabilities:
		None

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 0 1
	Current Speed: Unknown
	Type: Other
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: None
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A2
	Bank Connections: 4 5
	Current Speed: Unknown
	Type: Other
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A3
	Bank Connections: None
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x002D, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x002E, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002D
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x002F, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002D
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x0030, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002D
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: A2
	Bank Locator: Bank4/5
	Type: DDR2
	Type Detail: Synchronous
	Speed: 533 MHz
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x0031, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002D
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A3
	Bank Locator: Bank6/7
	Type: Unknown
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

```

---

### Post by typhoon_tip on 2012-10-16
OK, maximum memory you can install total is 4G. Each bank must be 1GB (same as the current one), DDR2, 533 Mhz. System reports that you have 4 banks available (1 occupied of course !).

Should not be difficult to find, they are still on sales (perhaps you can find some used ones as well).

Seems to me is a laptop you are talking about, they should be around 20$~25$ a piece.

---

### Post by Cheesemill on 2012-10-16
I read the output as saying that he has 2 x 1GB sticks installed with 2 free slots.

---

### Post by wheeze on 2012-10-16
> **Cheesemill said:**
> I read the output as saying that he has 2 x 1GB sticks installed with 2 free slots.

Correct.

---

### Post by unibroker on 2012-10-16
> **Cheesemill said:**
> I read the output as saying that he has 2 x 1GB sticks installed with 2 free slots.
I had the case open yesterday for cleaning and forgot to check the number of memory sticks.  I know my RAM total is 2GB.  I think somewhere I read that the number of GBs per slot needs to be the same as all other occupied slots.  So if I were to increase to 4GB total I would add 1GB sticks to the 2 remaining memory slots.

Thanks for all of the help posters!

---

