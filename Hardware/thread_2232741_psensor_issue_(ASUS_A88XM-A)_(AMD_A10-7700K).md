---
title: "psensor issue (ASUS A88XM-A) (AMD A10-7700K)"
date: 2014-07-03
forum: Hardware
---

### Post by presence2 on 2014-07-03
lubuntu 14 recent updates installed, FM2+ motherboard

I did everything here:

[http://digital-era.net/psensor-updated-with-option-to-display-temperature-sensors-on-the-panel-ubuntu-14-04-ppa/](http://digital-era.net/psensor-updated-with-option-to-display-temperature-sensors-on-the-panel-ubuntu-14-04-ppa/)

But I'm getting really weird readings:

[IMG]http://i.imgur.com/G3RMLXu.png[/IMG]



[IMG]http://i.imgur.com/EYr93ls.png[/IMG]

[IMG]http://i.imgur.com/BmlbtS5.png[/IMG]

---

### Post by sammiev on 2014-07-03
Wish my computer ran that cool. 

Post all the specs from your computer and if it's stored in a freezer.

---

### Post by presence2 on 2014-07-03
I've been meaning to do a full diagnostic on this new build... so here we go:

```


TABLE OF CONTENTS:
-----------------------------------------------

1) sudo uname -a
2) sudo hddtemp /dev/sda
3) sensors
4) sudo fdisk -l
5) free -m
6) grep MemTotal /proc/meminfo
7) cat /proc/meminfo
8) cat /proc/cpuinfo | grep "MHz"
9) sudo dmidecode -t processor | grep Speed
[FONT=Verdana]10) [/FONT]cat /var/log/kern.log | grep "MHz processor"
11) cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_max_freq 
12) acpi -V
13) df -h
14) ./speedtest-cli [redacted]
15) mount
16) lspci -v
17) sudo lshw


FULL DIAGNOSTICS REPORT:
-----------------------------------------------
(per subsections above, let me know if you need anything else):

11111111111111111111
sudo uname -a
-----------------------------------------------
Linux oracle-System-Product-Name 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:47:59 UTC 2014 i686 athlon i686 GNU/Linux

22222222222222222222
sudo hddtemp /dev/sda
-----------------------------------------------

/dev/sda: ST3250318AS: 36°C

3333333333333333333
sensors
-----------------------------------------------

radeon-pci-0008
Adapter: PCI adapter
temp1: +0.0°C 

k10temp-pci-00c3
Adapter: PCI adapter
temp1: +4.1°C (high = +70.0°C)
(crit = +70.0°C, hyst = +69.0°C)

444444444444444444444444
sudo fdisk -l
-----------------------------------------------

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006c53a

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 473839615 236918784 83 Linux
/dev/sda2 473841662 488396799 7277569 5 Extended
/dev/sda5 473841664 488396799 7277568 82 Linux swap / Solaris

555555555555555555555
free -m
---------------------------------------------

total used free shared buffers cached
Mem: 7011 1440 5571 32 48 589
-/+ buffers/cache: 802 6209
Swap: 7106 0 7106

666666666666666666666
grep MemTotal /proc/meminfo
-----------------------------------------------------

MemTotal: 7179828 kB


777777777777777777777
cat /proc/meminfo
---------------------------------------------------

MemTotal: 7179828 kB
MemFree: 5726920 kB
Buffers: 49600 kB
Cached: 607208 kB
SwapCached: 0 kB
Active: 955736 kB
Inactive: 405400 kB
Active(anon): 705260 kB
Inactive(anon): 36204 kB
Active(file): 250476 kB
Inactive(file): 369196 kB
Unevictable: 0 kB
Mlocked: 0 kB
HighTotal: 6365804 kB
HighFree: 5079712 kB
LowTotal: 814024 kB
LowFree: 647208 kB
SwapTotal: 7277564 kB
SwapFree: 7277564 kB
Dirty: 64 kB
Writeback: 0 kB
AnonPages: 704324 kB
Mapped: 148396 kB
Shmem: 37140 kB
Slab: 41708 kB
SReclaimable: 25924 kB
SUnreclaim: 15784 kB
KernelStack: 3000 kB
PageTables: 9288 kB
NFS_Unstable: 0 kB
Bounce: 0 kB
WritebackTmp: 0 kB
CommitLimit: 10867476 kB
Committed_AS: 2432408 kB
VmallocTotal: 122880 kB
VmallocUsed: 41812 kB
VmallocChunk: 75360 kB
HardwareCorrupted: 0 kB
AnonHugePages: 206848 kB
HugePages_Total: 0
HugePages_Free: 0
HugePages_Rsvd: 0
HugePages_Surp: 0
Hugepagesize: 2048 kB
DirectMap4k: 30712 kB
DirectMap2M: 882688 kB

88888888888888888888888888
cat /proc/cpuinfo | grep "MHz"
-------------------------------------------------------

cpu MHz : 2000.000
cpu MHz : 2000.000
cpu MHz : 2000.000
cpu MHz : 3400.000

99999999999999999999999999
sudo dmidecode -t processor | grep Speed
----------------------------------------------------------------

Max Speed: 3400 MHz
Current Speed: 3400 MHz

101010101010101010
cat /var/log/kern.log | grep "MHz processor"
--------------------------------------------------------------------

Jun 30 23:22:55 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.106 MHz processor
Jun 30 23:39:32 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3416.755 MHz processor
Jul 1 07:38:10 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3416.970 MHz processor
Jul 1 07:42:58 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.178 MHz processor
Jul 1 07:48:36 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.030 MHz processor
Jul 2 06:27:43 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3416.825 MHz processor
Jul 2 13:08:37 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.164 MHz processor
Jul 2 13:11:41 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.006 MHz processor
Jul 3 10:51:20 oracle-System-Product-Name kernel: [ 0.012000] tsc: Detected 3416.960 MHz processor
Jul 3 19:15:48 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3416.754 MHz processor
Jul 3 21:29:08 oracle-System-Product-Name kernel: [ 0.004000] tsc: Detected 3417.043 MHz processor


1111111111111111111111111111111
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_max_freq 
------------------------------------------------------

3400000
3400000
3400000
3400000

1212121212121212121212
acpi -V
-----------------------------------------------------

No support for device type: power_supply
No support for device type: power_supply
Cooling 0: Processor 0 of 10
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10

131313131313131313
df -h
----------------------------------------------------

Filesystem Size Used Avail Use% Mounted on
/dev/sda1 223G 3.8G 208G 2% /
none 4.0K 0 4.0K 0% /sys/fs/cgroup
udev 3.5G 4.0K 3.5G 1% /dev
tmpfs 702M 1.1M 701M 1% /run
none 5.0M 0 5.0M 0% /run/lock
none 3.5G 30M 3.4G 1% /run/shm
none 100M 20K 100M 1% /run/user


1414141414141414
./speedtest-cli
----------------------------------------------------------


Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from XXX (X.X.X.X)...
Selecting best server based on ping...
Hosted by XXX (XXX, XX) [100.85 km]: 18.597 ms
Testing download speed........................................
Download: 3.25 Mbits/s
Testing upload speed..................................................
Upload: 0.43 Mbits/s

151515151515151515
mount
------------------------------------------------

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=xxxx)

16161616161616
lspci -v
---------------------------------------------------------


00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1422
Subsystem: ASUSTeK Computer Inc. Device 85cb
Flags: bus master, fast devsel, latency 0


00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R7 200 Series] (prog-if 00 [VGA controller])
Subsystem: ASUSTeK Computer Inc. Device 85cb
Flags: bus master, fast devsel, latency 0, IRQ 84
Memory at e0000000 (64-bit, prefetchable) 
Memory at f0000000 (64-bit, prefetchable) 
I/O ports at f000 
Memory at feb00000 (32-bit, non-prefetchable) 
Expansion ROM at feb40000 [disabled] 
Capabilities: <access denied>
Kernel driver in use: radeon


00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1308
Subsystem: ASUSTeK Computer Inc. Device 85cb
Flags: bus master, fast devsel, latency 0, IRQ 85
Memory at feb64000 (64-bit, non-prefetchable) 
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel


00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
Flags: fast devsel


00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
Flags: fast devsel


00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1424
Flags: fast devsel


00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09) (prog-if 30 [XHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, fast devsel, latency 0, IRQ 18
Memory at feb6a000 (64-bit, non-prefetchable) 
Capabilities: <access denied>
Kernel driver in use: xhci_hcd


00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09) (prog-if 30 [XHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at feb68000 (64-bit, non-prefetchable) 
Capabilities: <access denied>
Kernel driver in use: xhci_hcd


00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 82
I/O ports at f140 
I/O ports at f130 [size=4]
I/O ports at f120 [size=8]
I/O ports at f110 [size=4]
I/O ports at f100 [size=16]
Memory at feb70000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
Kernel driver in use: ahci


00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
Memory at feb6f000 (32-bit, non-prefetchable) [size=4K]
Kernel driver in use: ohci-pci


00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
Memory at feb6e000 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>
Kernel driver in use: ehci-pci


00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
Memory at feb6d000 (32-bit, non-prefetchable) [size=4K]
Kernel driver in use: ohci-pci


00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
Memory at feb6c000 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>
Kernel driver in use: ehci-pci


00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: 66MHz, medium devsel
Kernel driver in use: piix4_smbus


00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
Subsystem: ASUSTeK Computer Inc. Device 8576
Flags: bus master, slow devsel, latency 32, IRQ 16
Memory at feb60000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel


00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
Subsystem: ASUSTeK Computer Inc. Device 85ca
Flags: bus master, 66MHz, medium devsel, latency 0


00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Bus: primary=00, secondary=01, subordinate=01, sec-latency=64


00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
Capabilities: <access denied>
Kernel driver in use: pcieport


00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: fea00000-feafffff
Prefetchable memory behind bridge: 00000000f0800000-00000000f08fffff
Capabilities: <access denied>
Kernel driver in use: pcieport


00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141a
Flags: fast devsel


00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141b
Flags: fast devsel


00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141c
Flags: fast devsel


00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141d
Flags: fast devsel
Capabilities: <access denied>
Kernel driver in use: k10temp


00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141e
Flags: fast devsel


00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 141f
Flags: fast devsel


03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
Subsystem: ASUSTeK Computer Inc. Device 8554
Flags: bus master, fast devsel, latency 0, IRQ 83
I/O ports at e000 [size=256]
Memory at fea00000 (64-bit, non-prefetchable) [size=4K]
Memory at f0800000 (64-bit, prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: r8169

171717171717
sudo lshw
-------------------------------------------------


oracle-system-product-name
description: Desktop Computer
product: System Product Name (SKU)
vendor: System manufacturer
version: System Version
serial: System Serial Number
width: 32 bits
capabilities: smbios-2.7 dmi-2.7 smp-1.4 smp
configuration: boot=normal chassis=desktop cpus=4 family=To be filled by O.E.M. sku=SKU uuid=0E68279D-786E-F300-62AB-D850E63F1882
*-core
[SIZE=5]description: Motherboard
product: A88XM-A
[SIZE=5]vendor: ASUSTeK COMPUTER INC.
physical id: 0
version: Rev X.0x
serial: 130916103401299
slot: To be filled by O.E.M.
*-firmware
description: BIOS
vendor: American Megatrends Inc.
physical id: 0
version: 0603
date: 10/16/2013
size: 64KiB
capacity: 8128KiB
capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
*-memory
description: System Memory
physical id: 24
slot: System board or motherboard
[SIZE=5]size: 8GiB
*-bank:0
[SIZE=5]description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
product: Array1_PartNumber1
vendor: A1_Manufacturer1
physical id: 0
serial: A1_SerNum1
slot: DIMM_A1
size: 4GiB
width: 64 bits
clock: 1600MHz (0.6ns)
*-bank:1
description: [empty]
product: Array1_PartNumber0
vendor: A1_Manufacturer0
physical id: 1
serial: A1_SerNum0
slot: DIMM_A2
*-bank:2
description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
product: BLS4G3D1609DS1S00.
vendor: Undefined
physical id: 2
serial: AD0195EA
slot: DIMM_B1
size: 4GiB
width: 64 bits
clock: 1600MHz (0.6ns)
*-bank:3
description: [empty]
product: Array1_PartNumber3
vendor: A1_Manufacturer3
physical id: 3
serial: A1_SerNum3
slot: DIMM_B2
*-cache:0
description: L1 cache
physical id: 32
slot: L1 CACHE
size: 256KiB
capacity: 256KiB
clock: 1GHz (1.0ns)
capabilities: pipeline-burst internal write-back unified
*-cache:1
description: L2 cache
physical id: 33
slot: L2 CACHE
size: 4MiB
capacity: 4MiB
clock: 1GHz (1.0ns)
capabilities: pipeline-burst internal write-back unified
*-cpu:0
[SIZE=5]description: CPU
product: AMD A10-7700K APU with Radeon(TM) R7 Graphics
vendor: Advanced Micro Devices [AMD]
physical id: 3c
bus info: cpu@0
version: 15.0.1
slot: FM2+
size: 2GHz
capacity: 3400MHz
width: 64 bits
clock: 100MHz
capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc nonstop_tsc extd_apicid aperfmperf eagerfpu pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb xsaveopt hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold fsgsbase bmi1 cpufreq
configuration: cores=4 enabledcores=4 threads=4
*-cpu:1
physical id: 1
bus info: cpu@1
version: 15.0.1
size: 2GHz
capacity: 2GHz
capabilities: cpufreq
*-cpu:2
physical id: 2
bus info: cpu@2
version: 15.0.1
size: 2GHz
capacity: 2GHz
capabilities: cpufreq
*-cpu:3
physical id: 3
bus info: cpu@3
version: 15.0.1
size: 2GHz
capacity: 2GHz
capabilities: cpufreq
*-pci:0
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 100
bus info: pci@0000:00:00.0
version: 00
width: 32 bits
clock: 33MHz
*-display
description: VGA compatible controller
product: Kaveri [Radeon R7 200 Series]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 1
bus info: pci@0000:00:01.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
resources: irq:84 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:feb40000-feb5ffff
*-multimedia:0
description: Audio device
product: Advanced Micro Devices, Inc. [AMD/ATI]
vendor: Advanced Micro Devices, Inc. [AMD/ATI]
physical id: 1.1
bus info: pci@0000:00:01.1
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm pciexpress msi bus_master cap_list
configuration: driver=snd_hda_intel latency=0
resources: irq:85 memory:feb64000-feb67fff
*-usb:0
description: USB controller
product: FCH USB XHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 10
bus info: pci@0000:00:10.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: pm msi msix pciexpress xhci bus_master cap_list
configuration: driver=xhci_hcd latency=0
resources: irq:18 memory:feb6a000-feb6bfff
*-usb:1
description: USB controller
product: FCH USB XHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 10.1
bus info: pci@0000:00:10.1
version: 09
width: 64 bits
clock: 33MHz
capabilities: pm msi msix pciexpress xhci bus_master cap_list
configuration: driver=xhci_hcd latency=0
resources: irq:17 memory:feb68000-feb69fff
*-storage
description: SATA controller
product: FCH SATA Controller [AHCI mode]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 11
bus info: pci@0000:00:11.0
version: 40
width: 32 bits
clock: 66MHz
capabilities: storage msi ahci_1.0 bus_master cap_list
configuration: driver=ahci latency=32
resources: irq:82 ioport:f140(size=8) ioport:f130(size=4) ioport:f120(size=8) ioport:f110(size=4) ioport:f100(size=16) memory:feb70000-feb707ff
*-usb:2
description: USB controller
product: FCH USB OHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 12
bus info: pci@0000:00:12.0
version: 11
width: 32 bits
clock: 66MHz
capabilities: ohci bus_master
configuration: driver=ohci-pci latency=32
resources: irq:18 memory:feb6f000-feb6ffff
*-usb:3
description: USB controller
product: FCH USB EHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 12.2
bus info: pci@0000:00:12.2
version: 11
width: 32 bits
clock: 66MHz
capabilities: pm debug ehci bus_master cap_list
configuration: driver=ehci-pci latency=32
resources: irq:17 memory:feb6e000-feb6e0ff
*-usb:4
description: USB controller
product: FCH USB OHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 13
bus info: pci@0000:00:13.0
version: 11
width: 32 bits
clock: 66MHz
capabilities: ohci bus_master
configuration: driver=ohci-pci latency=32
resources: irq:18 memory:feb6d000-feb6dfff
*-usb:5
description: USB controller
product: FCH USB EHCI Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 13.2
bus info: pci@0000:00:13.2
version: 11
width: 32 bits
clock: 66MHz
capabilities: pm debug ehci bus_master cap_list
configuration: driver=ehci-pci latency=32
resources: irq:17 memory:feb6c000-feb6c0ff
*-serial
description: SMBus
product: FCH SMBus Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 14
bus info: pci@0000:00:14.0
version: 16
width: 32 bits
clock: 66MHz
configuration: driver=piix4_smbus latency=0
resources: irq:0
*-multimedia:1
description: Audio device
product: FCH Azalia Controller
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 14.2
bus info: pci@0000:00:14.2
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=snd_hda_intel latency=32
resources: irq:16 memory:feb60000-feb63fff
*-isa
description: ISA bridge
product: FCH LPC Bridge
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 14.3
bus info: pci@0000:00:14.3
version: 11
width: 32 bits
clock: 66MHz
capabilities: isa bus_master
configuration: latency=0
*-pci:0
description: PCI bridge
product: FCH PCI Bridge
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 14.4
bus info: pci@0000:00:14.4
version: 40
width: 32 bits
clock: 66MHz
capabilities: pci subtractive_decode bus_master vga_palette
*-pci:1
description: PCI bridge
product: Hudson PCI to PCI bridge (PCIE port 0)
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 15
bus info: pci@0000:00:15.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:17
*-pci:2
description: PCI bridge
product: Hudson PCI to PCI bridge (PCIE port 2)
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 15.2
bus info: pci@0000:00:15.2
version: 00
width: 32 bits
clock: 33MHz
capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:17 ioport:e000(size=4096) memory:fea00000-feafffff ioport:f0800000(size=1048576)
*-network
description: Ethernet interface
product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 0c
serial: d8:50:e6:3f:18:82
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.2.150 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
resources: irq:83 ioport:e000(size=256) memory:fea00000-fea00fff memory:f0800000-f0803fff
*-pci:1
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 101
bus info: pci@0000:00:02.0
version: 00
width: 32 bits
clock: 33MHz
*-pci:2
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 102
bus info: pci@0000:00:03.0
version: 00
width: 32 bits
clock: 33MHz
*-pci:3
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 103
bus info: pci@0000:00:04.0
version: 00
width: 32 bits
clock: 33MHz
*-pci:4
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 104
bus info: pci@0000:00:18.0
version: 00
width: 32 bits
clock: 33MHz
*-pci:5
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 105
bus info: pci@0000:00:18.1
version: 00
width: 32 bits
clock: 33MHz
*-pci:6
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 106
bus info: pci@0000:00:18.2
version: 00
width: 32 bits
clock: 33MHz
*-pci:7
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 107
bus info: pci@0000:00:18.3
version: 00
width: 32 bits
clock: 33MHz
configuration: driver=k10temp
resources: irq:0
*-pci:8
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 108
bus info: pci@0000:00:18.4
version: 00
width: 32 bits
clock: 33MHz
*-pci:9
description: Host bridge
product: Advanced Micro Devices, Inc. [AMD]
vendor: Advanced Micro Devices, Inc. [AMD]
physical id: 109
bus info: pci@0000:00:18.5
version: 00
width: 32 bits
clock: 33MHz
*-scsi:0
physical id: 4
logical name: scsi0
capabilities: emulated
*-disk
description: ATA Disk
[SIZE=5]product: ST3250318AS
vendor: Seagate
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: CC66
serial: 6VY6F8Q4
[SIZE=5]size: 232GiB (250GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 sectorsize=512 signature=0006c53a
*-volume:0
description: EXT4 volume
vendor: Linux
physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
logical name: /
version: 1.0
serial: 83b7608a-c08e-4492-90de-46ea3a1b92ac
size: 225GiB
capacity: 225GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
configuration: created=2014-06-30 23:14:08 filesystem=ext4 lastmountpoint=/ modified=2014-07-03 19:15:47 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-07-03 19:15:47 state=mounted
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@0:0.0.0,2
[SIZE=5]logical name: /dev/sda2
capacity: 7107MiB
size: 7107MiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 7107MiB
capabilities: nofs
*-scsi:1
physical id: 5
logical name: scsi1
capabilities: emulated
*-cdrom
description: DVD-RAM writer
product: DVDRAM GH24NSB0
vendor: HL-DT-ST
physical id: 0.0.0
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/sr0
version: LN00
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 status=nodisc

sudo sensors-detect 
--------------------------------------------

# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# Board: ASUSTeK COMPUTER INC. A88XM-A


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595... No
VIA VT82C686 Integrated Sensors... No
VIA VT8231 Integrated Sensors... No
AMD K8 thermal sensors... No
AMD Family 10h thermal sensors... No
AMD Family 11h thermal sensors... No
AMD Family 12h and 14h thermal sensors... No
AMD Family 15h thermal sensors... No
AMD Family 15h power sensors... No
AMD Family 16h power sensors... No
Intel digital thermal sensor... No
Intel AMB FB-DIMM thermal sensor... No
VIA C7 thermal sensor... No
VIA Nano thermal sensor... No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'... No
Trying family `SMSC'... No
Trying family `VIA/Winbond/Nuvoton/Fintek'... No
Trying family `ITE'... Yes
Found unknown chip with ID 0x8603
(logical device 4 has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'... No
Trying family `SMSC'... No
Trying family `VIA/Winbond/Nuvoton/Fintek'... No
Trying family `ITE'... No


Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0... No
Probing for `IPMI BMC SMIC' at 0xca8... No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290... No
Probing for `National Semiconductor LM79' at 0x290... No
Probing for `Winbond W83781D' at 0x290... No
Probing for `Winbond W83782D' at 0x290... No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-piix4' for device 0000:00:14.0: AMD Hudson-2 SMBus


Next adapter: Radeon i2c bit bus 0x90 (i2c-0)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x91 (i2c-1)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x92 (i2c-2)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x93 (i2c-3)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x94 (i2c-4)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x95 (i2c-5)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon aux bus DP-auxch (i2c-6)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-7)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'... No
Probing for `Analog Devices ADM1034'... No
Probing for `SPD EEPROM'... Yes
(confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'... No
Client found at address 0x51
Probing for `Analog Devices ADM1033'... No
Probing for `Analog Devices ADM1034'... No
Probing for `SPD EEPROM'... Yes
(confidence 8, not a hardware monitoring chip)


Next adapter: SMBus PIIX4 adapter at 0b20 (i2c-8)
Do you want to scan it? (YES/no/selectively): y


Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.
```

---

### Post by presence2 on 2014-07-03
hmmmm...

so I just re ran

sudo sensors-detect

...last time I just y y y my way through... but this time I read everything as it went by and noticed this final output:

> Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

here is the full output

```
sudo sensors-detect 

# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# Board: ASUSTeK COMPUTER INC. A88XM-A


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595... No
VIA VT82C686 Integrated Sensors... No
VIA VT8231 Integrated Sensors... No
AMD K8 thermal sensors... No
AMD Family 10h thermal sensors... No
AMD Family 11h thermal sensors... No
AMD Family 12h and 14h thermal sensors... No
AMD Family 15h thermal sensors... No
AMD Family 15h power sensors... No
AMD Family 16h power sensors... No
Intel digital thermal sensor... No
Intel AMB FB-DIMM thermal sensor... No
VIA C7 thermal sensor... No
VIA Nano thermal sensor... No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'... No
Trying family `SMSC'... No
Trying family `VIA/Winbond/Nuvoton/Fintek'... No
Trying family `ITE'... Yes
Found unknown chip with ID 0x8603
(logical device 4 has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'... No
Trying family `SMSC'... No
Trying family `VIA/Winbond/Nuvoton/Fintek'... No
Trying family `ITE'... No


Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0... No
Probing for `IPMI BMC SMIC' at 0xca8... No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290... No
Probing for `National Semiconductor LM79' at 0x290... No
Probing for `Winbond W83781D' at 0x290... No
Probing for `Winbond W83782D' at 0x290... No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-piix4' for device 0000:00:14.0: AMD Hudson-2 SMBus


Next adapter: Radeon i2c bit bus 0x90 (i2c-0)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x91 (i2c-1)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x92 (i2c-2)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x93 (i2c-3)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x94 (i2c-4)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon i2c bit bus 0x95 (i2c-5)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: Radeon aux bus DP-auxch (i2c-6)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-7)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'... No
Probing for `Analog Devices ADM1034'... No
Probing for `SPD EEPROM'... Yes
(confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'... No
Client found at address 0x51
Probing for `Analog Devices ADM1033'... No
Probing for `Analog Devices ADM1034'... No
Probing for `SPD EEPROM'... Yes
(confidence 8, not a hardware monitoring chip)


Next adapter: SMBus PIIX4 adapter at 0b20 (i2c-8)
Do you want to scan it? (YES/no/selectively): y


Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.

```

[COLOR=#000000]*Trying family `ITE'... Yes*[/COLOR]
[COLOR=#800080][I][B]Found unknown chip with ID 0x8603
[/B][/I][/COLOR]Sorry, no sensors were detected.

No sensors on an ASUS [COLOR=#000000]A88XM-A with [/COLOR][COLOR=#000000]AMD A10-7700K APU 

???

I'm confused.

my 30 day warranty is running out on the mobo should I be concerned?  [/COLOR]

---

### Post by Yellow Pasque on 2014-07-04
It looks like you have an ITE IT8603E chip:
```
Trying family `ITE'... Yes
Found unknown chip with ID 0x8603
```

You need to use a newer kernel or build the standalone module for that chip: [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

As for the CPu sensor, newer kernel should help there too: [https://github.com/torvalds/linux/commit/d303b1b5fbb688282bbf72a534b9dfed7af9fe4f](https://github.com/torvalds/linux/commit/d303b1b5fbb688282bbf72a534b9dfed7af9fe4f)

---

### Post by presence2 on 2014-07-05
```
sudo uname -a
Linux oracle-System-Product-Name 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:47:59 UTC 2014 i686 athlon i686 GNU/Linux
```

I'm not sure I understand:  What family is my chip and what kernel do I need?

Pertinent section from your link:

[TABLE="class: wiki"]
[TR]
[TD][ AMD]("http://www.amd.com/")[/TD]
[TD]K8[/TD]
[TD]yes[/TD]
[TD]k8temp[/TD]
[TD]PCI[/TD]
[TD]2.6.19 or[ standalone driver]("http://jdelvare.nerim.net/devel/lm-sensors/drivers/k8temp/")[/TD]
[TD]Latest AMD K8 processors have integrated sensors which can be read directly without any additional monitoring chip. Driver contributed by Rudolf Marek. Upgrade to lm_sensors 2.10.1 or later is mandatory, earlier versions of libsensors will fail with a "General parse error" message. **Note: many recent K8 models (revision F and later) have been reported to have broken thermal sensors so the k8temp driver will return bogus values. See ticket[#2278]("http://www.lm-sensors.org/ticket/2278") for example. Changes in kernel 2.6.29 may improve the situation a bit. Feedback welcome.** See this [FAQ entry]("http://www.lm-sensors.org/wiki/FAQ/Chapter3#AMDK8supportin2.6.33and2.6.34kernels") if running kernel 2.6.33 or 2.6.34 on a rev. G desktop model.[/TD]
[/TR]
[TR]
[TD][ AMD]("http://www.amd.com/")[/TD]
[TD]Family 10h CPU, family 11h CPU[/TD]
[TD]yes[/TD]
[TD]k10temp[/TD]
[TD]PCI[/TD]
[TD]2.6.33 or[ standalone driver]("http://jdelvare.nerim.net/devel/lm-sensors/drivers/k10temp/")[/TD]
[TD](2009-12-06) Embedded sensors are known to be unreliable on the DR-BA, DR-B2, DR-B3, RB-C2 and HY-D0 revisions of the family 10h CPU, which will never be supported. Driver contributed by Clemens Ladisch, reviewed by Jean Delvare.[/TD]
[/TR]
[TR]
[TD][ AMD]("http://www.amd.com/")[/TD]
[TD]Family 12h CPU, family 14h CPU[/TD]
[TD]yes[/TD]
[TD]k10temp[/TD]
[TD]PCI[/TD]
[TD]2.6.38 or[ standalone driver]("http://jdelvare.nerim.net/devel/lm-sensors/drivers/k10temp/")[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][ AMD]("http://www.amd.com/")[/TD]
[TD]Family 15h CPU[/TD]
[TD]yes[/TD]
[TD]k10temp, fam15h_power[/TD]
[TD]PCI[/TD]
[TD]3.0 or[ standalone driver]("http://jdelvare.nerim.net/devel/lm-sensors/drivers/k10temp/")[/TD]
[TD](2014-03-12) Power monitoring driver contributed by Andreas Herrmann (AMD), reviewed by Jean Delvare. **Note: we have had reports of [ completely wrong values]("http://lists.lm-sensors.org/pipermail/lm-sensors/2011-November/034243.html") being reported by the fam15h_power driver on some systems. See [ here]("http://lists.lm-sensors.org/pipermail/lm-sensors/2012-January/034905.html") for a hint.** Kaveri support added in kernel 3.14.[/TD]
[/TR]
[TR]
[TD][ AMD]("http://www.amd.com/")[/TD]
[TD]Family 16h CPU[/TD]
[TD]yes[/TD]
[TD]k10temp, fam15h_power[/TD]
[TD]PCI[/TD]
[TD]3.7.1[/TD]
[TD](2014-03-12) Kabini support added in kernel 3.12. Mullins support added in kernel 3.15.[/TD]
[/TR]
[/TABLE]



What do I do with this:

[COLOR=#555555][FONT=Consolas]drivers/hwmon/k10temp.c[/FONT][/COLOR][COLOR=#555555][View]("https://github.com/torvalds/linux/blob/d303b1b5fbb688282bbf72a534b9dfed7af9fe4f/drivers/hwmon/k10temp.c")

[/COLOR]

[TABLE="class: file-code file-diff tab-size-8 hide-line-numbers line-number-attrs, width: 918"]
[TR="class: file-diff-line gc, bgcolor: #EAF2F5"]
[TD="class: diff-line-num expandable-line-num, bgcolor: #F3F3FF, colspan: 2, align: center"][/TD]
[TD="class: diff-line-code, bgcolor: #F8F8FF"]@@ -210,6 +210,7 @@ static const struct pci_device_id k10temp_id_table[] = {[/TD]
[/TR]
[TR="class: file-diff-line js-file-line"]
[TD="class: diff-line-num linkable-line-number, bgcolor: #F6E8B5, align: right"][/TD]
[TD="class: diff-line-num linkable-line-number, bgcolor: #F6E8B5, align: right"][/TD]
[TD="class: diff-line-code, bgcolor: #F8EEC7"]     { PCI_VDEVICE(AMD, PCI_DEVICE_ID_AMD_CNB17H_F3) },[/TD]
[/TR]
[TR="class: file-diff-line js-file-line"]
[TD="class: diff-line-num linkable-line-number, align: right"][/TD]
[TD="class: diff-line-num linkable-line-number, align: right"][/TD]
[TD="class: diff-line-code"]     { PCI_VDEVICE(AMD, PCI_DEVICE_ID_AMD_15H_NB_F3) },[/TD]
[/TR]
[TR="class: file-diff-line js-file-line"]
[TD="class: diff-line-num linkable-line-number, align: right"][/TD]
[TD="class: diff-line-num linkable-line-number, align: right"][/TD]
[TD="class: diff-line-code"]     { PCI_VDEVICE(AMD, PCI_DEVICE_ID_AMD_15H_M10H_F3) },[/TD]
[/TR]
[TR="class: file-diff-line js-file-line gi, bgcolor: #DDFFDD"]
[TD="class: diff-line-num empty-cell, bgcolor: #CEFFCE, align: right"][/TD]
[TD="class: diff-line-num linkable-line-number, bgcolor: #CEFFCE, align: right"][/TD]
[TD="class: diff-line-code"]+    { PCI_VDEVICE(AMD, PCI_DEVICE_ID_AMD_15H_M30H_NB_F3) },[/TD]
[/TR]
[TR="class: file-diff-line js-file-line"]
[TD="class: diff-line-num linkable-line-number, align: right"][/TD]
[TD="class: diff-line-num linkable-line-number, align: right"][/TD]
[TD="class: diff-line-code"]     { PCI_VDEVICE(AMD, PCI_DEVICE_ID_AMD_16H_NB_F3) },[/TD]
[/TR]
[TR="class: file-diff-line js-file-line"]
[TD="class: diff-line-num linkable-line-number, align: right"][/TD]
[TD="class: diff-line-num linkable-line-number, align: right"][/TD]
[TD="class: diff-line-code"]     {}[/TD]
[/TR]
[TR="class: file-diff-line js-file-line"]
[TD="class: diff-line-num linkable-line-number, align: right"][/TD]
[TD="class: diff-line-num linkable-line-number, align: right"][/TD]
[TD="class: diff-line-code"] };[/TD]
[/TR]
[TR="class: file-diff-line gc, bgcolor: #EAF2F5"]
[TD="class: diff-line-num expandable-line-num, bgcolor: #F3F3FF, colspan: 2, align: center"][/TD]
[/TR]
[/TABLE]



Do I need to install this code?   If so, where and how?

[https://github.com/torvalds/linux/blob/d303b1b5fbb688282bbf72a534b9dfed7af9fe4f/drivers/hwmon/k10temp.c](https://github.com/torvalds/linux/blob/d303b1b5fbb688282bbf72a534b9dfed7af9fe4f/drivers/hwmon/k10temp.c)

[http://jdelvare.nerim.net/devel/lm-sensors/drivers/k10temp/k10temp.c](http://jdelvare.nerim.net/devel/lm-sensors/drivers/k10temp/k10temp.c)

---

### Post by presence2 on 2014-07-05
[B]
[SIZE=5]
I FOUND THIS:[/SIZE][/B][URL="http://ubuntuforums.org/showthread.php?t=1287819"]

http://ubuntuforums.org/showthread.php?t=1287819[/URL]

^^^ is this what I need to do to get psensor working?

```
mkdir -p 'k10temp'
cd 'k10temp'
```

---

### Post by Yellow Pasque on 2014-07-05
The easiest way is to try a newer kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15.3-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15.3-utopic/)
Instructions: [https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels)

Once you boot into new kernel, run:
```
sudo modprobe -v it87
sensors
```

---

### Post by gordintoronto on 2014-07-05
sudo lshw -c cpu 

[http://cpuboss.com/cpu/AMD-A10-7700K](http://cpuboss.com/cpu/AMD-A10-7700K) says the CPU was released this year, so it might not be fully supported yet.

---

