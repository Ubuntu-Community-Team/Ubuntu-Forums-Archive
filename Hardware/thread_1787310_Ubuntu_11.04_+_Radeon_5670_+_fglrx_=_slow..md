---
title: "Ubuntu 11.04 + Radeon 5670 + fglrx = slow."
date: 2011-06-21
forum: Hardware
---

### Post by istaron on 2011-06-21
I'm a new user of Ubuntu. Before this i was using Windows systems, and Linux little bit(Debian, Gentoo, Arch). I have performanse issues in Ubuntu. Even in gedit, with syntax highlight. The using of system is unconfortable. With time the system starts to work even slower. I can't play in my favorite game Warcraft III, becouse i have low performanse in 800x600 resolution and minimal effects.

> orlan@orlan-GA-MA74GM-S2:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
5533 frames in 5.0 seconds = 1106.600 FPS
6330 frames in 5.0 seconds = 1266.000 FPS
6671 frames in 5.0 seconds = 1334.200 FPS
6608 frames in 5.0 seconds = 1321.600 FPS
6583 frames in 5.0 seconds = 1316.600 FPS
But i see < 5 FPS, 

> orlan@orlan-GA-MA74GM-S2:~$ glxgears 
12285 frames in 5.0 seconds = 2456.899 FPS
13164 frames in 5.0 seconds = 2632.768 FPS
12865 frames in 5.0 seconds = 2572.860 FPS
12624 frames in 5.0 seconds = 2524.710 FPS
12504 frames in 5.0 seconds = 2500.696 FPS
 same speed.

> orlan@orlan-GA-MA74GM-S2:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5670
OpenGL version string: 4.1.10834 Compatibility Profile Context

When i get this issue i'm install fglrx 11.6 and xorg edgers PPA, system began to work faster, but not enough.

AMD Athlon 64X2 5600+, 2Gb DDR2 800, Sapphire Radeon HD5670 512 mb, gygabyte MA74GM-S2 motherboard.

Sorry for my bad English.

---

### Post by istaron on 2011-06-21
Where i can get help?

---

### Post by jayjaytk on 2011-06-23
Just try to start Wc3 with the /opengl Parameter,

i.e. wine Frozen\ Throne.exe /opengl
or wine Warcraft\ III.exe /opengl

Good Luck

---

### Post by istaron on 2011-06-23
> **jayjaytk said:**
> Just try to start Wc3 with the /opengl Parameter,

i.e. wine Frozen\ Throne.exe /opengl
or wine Warcraft\ III.exe /opengl

Good Luck

Even with OpenGL there are brakes, but it is possible to play... The Problem is exist.

---

### Post by jayjaytk on 2011-06-23
Hallo,

tell me the output when you type 'free' in a console window.

and give me the output from 'cat /proc/cpuinfo' too.

---

### Post by istaron on 2011-06-23
> **jayjaytk said:**
> Hallo,

tell me the output when you type 'free' in a console window.

and give me the output from 'cat /proc/cpuinfo' too.

```

orlan@orlan-GA-MA74GM-S2:~$ free
             total       used       free     shared    buffers     cached
Mem:       2058044    1976736      81308          0      34896    1295548
-/+ buffers/cache:     646292    1411752
Swap:      2093052      59676    2033376

orlan@orlan-GA-MA74GM-S2:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 67
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping    : 3
cpu MHz        : 1000.000
cache size    : 1024 KB
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
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips    : 2013.74
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 67
model name    : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping    : 3
cpu MHz        : 1000.000
cache size    : 1024 KB
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
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips    : 2013.74
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```

```

orlan@orlan-GA-MA74GM-S2:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5670]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

---

### Post by jayjaytk on 2011-06-25
hallo,

your system is swapping what means that the amount of your ram isnt enough and the system is using the pagefile on your harddisk. this is much slower than doing that operations with the ram.

consider to buy some additional ram for your system, this will fix the problem that the system gets slower over the time. at the moment the price for ddr2 ram is very low (16 EUROS for 2 GB). i recommend a upgrade to 4 GB if you have the 32 bit version or to 6 GB if you have the 64 bit version.

if you dont wnat to buy something you can try to boot into ubuntu classic mode or identify your memory using processes by using 'top'.

---

### Post by istaron on 2011-06-25
I don't know why my system swapping, above resilts it's 2 days uptime. And all place populated by caches and buffers. Usually it's about 500 Mb in RAM (1.5 Gb free) and 0-5 Mb swap. Warcraft 3 needs in 300-400 Mb. I start it in nice --20, it's work better, but not perfect.

How you think, in other distros same situation with graphical performance?

---

### Post by jayjaytk on 2011-06-26
you can try a lightweight windowmanager that doesnt consumes so much ram as unity or gnome does.

my system has 4 gb ram and they are full in use even with the classic interface without effects.

i can run wc3 in opengl at > 60 frames per second and i have only a 4650 mobility graphic card, but a p8700 core 2 duo processor.

---

