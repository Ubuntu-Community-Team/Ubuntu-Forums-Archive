---
title: "Enabling multiprocessing 386 CPUs"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by akoong on 2007-05-11
I have an old Digital Celebris XL5133DP.

I have installed Ubuntu 6.06 on it. From the dmesg output (see below), only one of the two CPUs are recognised.

Is it possible to enable the second CPU also?

*************************

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000] BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[17179569.184000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000] BIOS-e820: 00000000000f5990 - 0000000000100000 (reserved)
[17179569.184000] BIOS-e820: 0000000000100000 - 000000000a000000 (usable)
[17179569.184000] BIOS-e820: 00000000fec00000 - 00000000fed00000 (reserved)
[17179569.184000] BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[17179569.184000] BIOS-e820: 00000000ffff5990 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 160MB LOWMEM available.
[17179569.184000] found SMP MP-table at 0009fc30
[17179569.184000] On node 0 totalpages: 40960
[17179569.184000] DMA zone: 4096 pages, LIFO batch:0
[17179569.184000] DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000] Normal zone: 36864 pages, LIFO batch:7
[17179569.184000] HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI not present.
[17179569.184000] Intel MultiProcessor Specification v1.1
[17179569.184000] Virtual Wire compatibility mode.
[17179569.184000] Default MP configuration #5
[17179569.184000] Processor #0 5:2 APIC version 16
[17179569.184000] Processor #1 5:2 APIC version 16
[17179569.184000] WARNING: NR_CPUS limit of 1 reached. Processor ignored.
[17179569.184000] I/O APIC #2 Version 16 at 0xFEC00000.
[17179569.184000] ISA/PCI bus type with no IRQ information... falling back to ELCR
[17179569.184000] Using ELCR to identify PCI interrupts
[17179569.184000] Processors: 1

---

### Post by [S2] on 2007-05-11
I have asimilar problem with an AMD Athlon(tm) 64 X2 Dual Core Processor 3800+:
cpuinfo sees only one core:
```
# cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2000.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 4022.28
clflush size    : 64
```
and uname -a does not show "SMP":
```
# uname -a
Linux black 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux
```
but the k8temp sensor for example sees both cpu temp sensors:
```
# sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +33 °C
Core1 Temp:
             +37 °C
```
this is with ubuntus 2.6.20-15-386 stock kernel. Does someone know what broke it?

---

### Post by [S2] on 2007-05-11
installing 2.6.20-15-generic solved the problem for me.

---

### Post by Ken_Lewis81 on 2007-05-11
The -generic kernel line is generally compiled with Symetric Multi-Processor (SMP) supprt.  Looking at [the base package list for Dapper]("http://packages.ubuntu.com/dapper/base/") there's no explicit statement that the default linux-image-386 is built for SMP.  I would expect that linux-image-server should be SMP-capable and would be surprised if linux-image-server-bigiron is not.  However, they most likely are built optimised for i686.

My suggestion then, would be to get linux-source-2.6.15 (via aptitude, etc.) and follow the [KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild) page at the Ubuntu Wiki, editing one file in the downloaded source directory, which should be in /usr/src/linux-image-2.6.15, but may be in your user's /home/*user*.  The file is the debian/config/i386/config.386 and you need to find and set "CONFIG_SMP=y" before you build your kernel.

take care.
Ken.

---

### Post by akoong on 2007-05-11
Thanks Ken.

I have downloaded the source from launchpad.net (linux-source-2.6.15_2.6.15-23.39_all.deb). Will give it a try as you suggested adn let you know how I go.

Thanks again

---

### Post by akoong on 2007-05-16
Hi Ken,

Tried the kernel rebuild and got the following error:

make[1]: Entering directory `/home/alan/linux-source-2.6.15-2.6.15/debian/build/build-386'
make[1]: Nothing to be done for `build'.
make[1]: Leaving directory `/home/alan/linux-source-2.6.15-2.6.15/debian/build/build-386'
ABI has changed!  Refusing to continue; please update the ABINAME accordingly.
Differences:
--- /home/alan/linux-source-2.6.15-2.6.15/debian/abi/2.6.15-28.52/i386/386
2007-05-15 08:01:25.000000000 +1000
+++ /home/alan/linux-source-2.6.15-2.6.15/debian/abi/2.6.15-28.53/i386/386
2007-05-16 19:43:36.000000000 +1000

make: *** [build] Error 1

=======================================


The build steps that I used is as follows:

	sudo apt-get install linux-kernel-devel fakeroot kernel-wedge kernel-package
	sudo apt-get build-dep linux-source
	apt-get source linux-image-2.6.15-27-386
	cd linux-image-2.6.15-27-386
	modify config.386 in debian/config/i386
	change CONFIG_SMP=y
	debian/bin/oldconfig i386
	AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=386


========================================

Would appreciate any advise as to how to fix the make error or any mistakes in my build steps.

---

### Post by Ken_Lewis81 on 2007-05-16
The thing that's stung you is the Kernel ABI Version.  This is an internal number that makes sure that the modules you load into the kernel will work -- ABI stands for Application Binary Interface.

This is stored in the debian/rules script in your kernel source directory.  It looks like you are building a new kernel with ABI number 53, but the debian/rules file thinks it's building version 52.  Change 52 to 53 and you should be good.  Check with the 'Kernel Version Mismatch' section under 'Building Linux-Restricted-Modules of [Ubuntu Custom Kernel Guide](https://wiki.ubuntu.com/KernelCustomBuild) at [wiki.ubuntu.com](wiki.ubuntu.com).

Good luck.
Take care.
Ken.

---

### Post by akoong on 2007-05-16
Thanks for the advice. Will give it a try toniight.

---

### Post by akoong on 2007-05-21
Hi Ken,

First the good news :) - Thanks to your help so far, I have successfully built the kernel and according to the dmesg output below both the processors are detected and initialised.

[17179569.184000] found SMP MP-table at 0009fc30
[17179569.184000] On node 0 totalpages: 40960
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 36864 pages, LIFO batch:7
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI not present.
[17179569.184000] Intel MultiProcessor Specification v1.1
[17179569.184000]     Virtual Wire compatibility mode.
[17179569.184000] Default MP configuration #5
[17179569.184000] Processor #0 5:2 APIC version 16
[17179569.184000] Processor #1 5:2 APIC version 16
[17179569.184000] I/O APIC #2 Version 16 at 0xFEC00000.
[17179569.184000] ISA/PCI bus type with no IRQ information... falling back to ELCR
[17179569.184000] Using ELCR to identify PCI interrupts
[17179569.184000] Processors: 2
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0a000000:f4c00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda1 ro quiet splash acpi=off
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 166.696 MHz processor.
[   90.760577] Using tsc for high-res timesource
[   90.762300] Console: colour VGA+ 80x25
[   90.767837] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   90.773975] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   90.854269] Memory: 151800k/163840k available (1890k kernel code, 11500k reserved, 604k data, 312k init, 0k highmem)
[   90.854350] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   90.934954] Calibrating delay using timer specific routine.. 334.77 BogoMIPS (lpj=669549)
[   90.935742] Security Framework v1.0.0 initialized
[   90.935835] SELinux:  Disabled at boot.
[   90.936153] Mount-cache hash table entries: 512
[   90.938539] CPU: After generic identify, caps: 000003bf 00000000 00000000 00000000 00000000 00000000 00000000
[   90.938649] CPU: After vendor identify, caps: 000003bf 00000000 00000000 00000000 00000000 00000000 00000000
[   90.938753] Intel Pentium with F0 0F bug - workaround enabled.
[   90.938814] CPU: After all inits, caps: 000003bf 00000000 00000000 00000000 00000000 00000000 00000000
[   90.939237] mtrr: v2.0 (20020519)
[   90.939297] Checking 'hlt' instruction... OK.
[   90.957209] checking if image is initramfs... it is
[  100.857588] Freeing initrd memory: 6702k freed
[  101.071099] CPU0: Intel Pentium 75 - 200 stepping 0c
[  101.071848] Booting processor 1/1 eip 2000
[  101.086556] Initializing CPU#1
[  101.164424] Calibrating delay using timer specific routine.. 333.38 BogoMIPS (lpj=666770)
[  101.164508] CPU: After generic identify, caps: 000003bf 00000000 00000000 00000000 00000000 00000000 00000000
[  101.164582] CPU: After vendor identify, caps: 000003bf 00000000 00000000 00000000 00000000 00000000 00000000
[  101.164670] CPU: After all inits, caps: 000003bf 00000000 00000000 00000000 00000000 00000000 00000000
[  101.164806] CPU1: Intel Pentium 75 - 200 stepping 0c
[  101.164967] Total of 2 processors activated (668.15 BogoMIPS).
[  101.165267] ExtINT not setup in hardware but reported by MP table
[  101.165409] ENABLING IO-APIC IRQs
[  101.165898] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[  101.312442] checking TSC synchronization across 2 CPUs: passed.
[    0.004211] Brought up 2 CPUs

=====================================================================


However when I issue the top command, it appears to show only one CPU is being used:

top - 20:17:05 up  2:03,  2 users,  load average: 0.32, 0.60, 0.46
Tasks:  70 total,   1 running,  69 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.2% us,  1.3% sy,  0.1% ni, 92.5% id,  0.9% wa,  0.0% hi,  0.0% si
Mem:    158964k total,   154792k used,     4172k free,    18916k buffers
Swap:   249572k total,        0k used,   249572k free,    58944k cached


Does this look right?

---

### Post by Ken_Lewis81 on 2007-05-21
Top shows an aggregate of your processing power -- the dmesg output would convince me that both processors are in use.  I think that this should be fixed, just check the output of the command ```
cat /proc/cpuinfo
```

take care.
Ken.

---

### Post by akoong on 2007-05-23
Hi Ken,

/proc/cpuinfo confirms that both the processors are recognised.

Looks like it worked :-)

Once again thanks for all your help. Wouldn't have doen it without it.

---

