---
title: "intel drivers"
date: 2011-12-14
forum: Hardware
---

### Post by crave-n on 2011-12-14
hi... i'm a newbie to ubuntu....
i want to know how to install the latest intel drivers for my desktop pc....
thanks in advance :)

---

### Post by josephmills on 2011-12-14
> **crave-n said:**
> hi... i'm a newbie to ubuntu....
i want to know how to install the latest intel drivers for my desktop pc....
thanks in advance :)

Sweet good idea. Could we see some more info about your system please open you terminal and enter 
```
lspci -nn && lsusb && cat /etc/proc/cpuinfo && free -a && df -h 
``` 
also 
```
sudo fdisk -l | awk '/identifier/ {print $3}';

```
lspci list all pci cards 
lsusb lists all usb pluins 
cat /etc/proc/cpuinfo    well..... 
free -a    shows us ram 
df -h       shows us the hardrives 
sudo fdisk -l | awk '/identifier/ {print $3}';
 gives us model # of hardrive 
thanks

---

### Post by crave-n on 2011-12-14
K.. this is wat i got frm runnin the code u gave:
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 10)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 10)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1094] (rev 01)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cat: /etc/proc/cpuinfo: No such file or directory
the model # of my hardware is:
0x00020e6c
0xb1a7b1a7

---

### Post by josephmills on 2011-12-14
> **crave-n said:**
> K.. this is wat i got frm runnin the code u gave:
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 10)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 10)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1094] (rev 01)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
cat: /etc/proc/cpuinfo: No such file or directory

sorry 
```
cat /proc/cpuinfo 
```  :popcorn:

---

### Post by crave-n on 2011-12-14
this is wat i got frm runnin the code again.....
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 10)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 10)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1094] (rev 01)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
stepping    : 13
cpu MHz        : 2000.000
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
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips    : 3999.77
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
stepping    : 13
cpu MHz        : 2000.000
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
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips    : 3999.90
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

free: invalid option -- 'a'
usage: free [-b|-k|-m|-g] [-l] [-o] [-t] [-s delay] [-c count] [-V]
  -b,-k,-m,-g show output in bytes, KB, MB, or GB
  -l show detailed low and high memory statistics
  -o use old format (no -/+buffers/cache line)
  -t display total for RAM + swap
  -s update every [delay] seconds
  -c update [count] times
  -V display version information and exit




THE MODEL # OF MY HARDWARE IS:
0x00020e6c
0xb1a7b1a7

---

### Post by Mark Phelps on 2011-12-15
This is Linux, not Windows.  In  Windows, the first thing you do after install is update your drivers; in Linux, you do not.

The correct Intel drivers were loaded during the initial Ubuntu setup.  You don't need to go hunting around for drivers now.

So, why do you feel you need to update the drivers?  Is something not working properly?

---

