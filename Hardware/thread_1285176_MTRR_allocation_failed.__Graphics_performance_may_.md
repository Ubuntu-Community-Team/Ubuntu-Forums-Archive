---
title: "MTRR allocation failed.  Graphics performance may suffer."
date: 2009-10-07
forum: Hardware
---

### Post by Beuntje on 2009-10-07
I've installed 9.10 beta and, I was looking trough my dmesg, and i found some failed issues.

Is this error a real error or is indeed my graphics slow.
I'm using an dell e6400 with a GM45 intel graphics card.

here is all the logging about drm in my dmesg

> [    8.615605] [drm] Initialized drm 1.1.0 20060810
[    9.287169] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    9.397775] [drm] i2c_init DPDDC-B
[    9.407512] [drm] i2c_init DPDDC-C
[    9.412573] [drm] i2c_init DPDDC-D
[    9.855300] [drm] TV-25: set mode NTSC 480i 0
[    9.981378] [drm] fb0: inteldrmfb frame buffer device
[   10.015416] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.090685] [drm] LVDS-8: set mode 1440x900 c
[   19.948015] [drm] TV-25: set mode NTSC 480i 0
[   20.089556] [drm] TV-25: set mode NTSC 480i 0
[   20.420755] [drm] TV-25: set mode NTSC 480i 0
[   20.560987] [drm] TV-25: set mode NTSC 480i 0
[   26.647059] [drm] TV-25: set mode NTSC 480i 0
[   26.788560] [drm] TV-25: set mode NTSC 480i 0
[   27.100861] [drm] TV-25: set mode NTSC 480i 0
[   27.242458] [drm] TV-25: set mode NTSC 480i 0
[   27.551157] [drm] TV-25: set mode NTSC 480i 0
[   27.691549] [drm] TV-25: set mode NTSC 480i 0
[   29.296634] [drm] TV-25: set mode NTSC 480i 0
[   29.437951] [drm] TV-25: set mode NTSC 480i 0


could someone explain what it means?
if it is a issue, please provide me a solution.

---

### Post by Beuntje on 2009-10-08
Nobody knows this ???
or can give me an answer?

---

### Post by sgerke on 2009-11-10
Hi,
I think it's the same problem I have with my Dell Latitude E4300 (4GB RAM). How much RAM do you have installed in your machine? Could you post the output of 
```
cat /proc/mtrr
```
please?

Best,
Sebastian

---

### Post by codfather on 2009-12-15
I'm seeing the exact same issue on the same hardware.

/proc/mtrr gives this.

```
reg00: base=0x000000000 (    0MB), size=32768MB, count=1: write-back
reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg02: base=0x0ddc00000 ( 3548MB), size=    4MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable
reg04: base=0x11c000000 ( 4544MB), size=   64MB, count=1: uncachable

```

I have tried several work arounds which include setting the following kernel boot commands
```

single enable_mtrr_cleanup 
mtrr_spare_reg_nr=1 
nopat

```

None of these have a positive affect.

The kernel that I'm currently running is:

2.6.31-16-generic-pae

The machine has 4GB RAM

Nick

---

### Post by Tobis87 on 2010-01-15
Hi,

The problem is that Reg00 covers all addressable ram, you'll have to split it smaller chunks, because you can't define an area as write-combining while it is already defined as write-back.

Could you also post the memory layout:
```
cat /proc/iomem
```

As well as the video area in which write-combining could be enabled:
```
#!/bin/sh
address=`lspci -v \
	| grep -A 7 VGA\
	| grep -F " prefetchable"\
	| awk 'BEGIN{OFS="";ORS=""}
	      {print $3
	      i = length($3)
	      while(i<8){
	      		print 0
	       		i++
	       }}'`

hsize=`lspci -v \
	| grep -A 7 VGA \
	| grep -F " prefetchable" \
	| awk '{print $6}' \
	| sed 's/[^0-9]//g' \
	| awk 'BEGIN {OFS = "";ORS=""}
	       { printf "%x" , $1
		 i = length($1)
		 while (i<8) {
		 	print 0
		 	i++
		 } }'`

echo "base=0x$address size=0x$hsize type=write-combining"
```

Reg00 seems to be wrong on every dell pc, mine also had the strange value of 65536MB.

**Edit:**

As far as I got /proc/mtrr should read:
```
reg00: base=0x00000000 (   0MB), size=2048MB, count=1: write-back
reg01: base=0x80000000 (2048MB), size=1024MB, count=1: write-back
reg02: base=0xc0000000 (3072MB), size= 512MB, count=1: write-back
reg03: base=0xddc00000 (3548MB), size=   4MB, count=1: uncachable
reg04: base=0xde000000 (3552MB), size=  32MB, count=1: uncachable
reg05: base=0xe0000000 (3584MB), size= 256MB, count=1: write-combining
reg06: base=0x100000000 (4096MB), size= 512MB, count=1: write-back
reg07: base=0x11c000000 (4544MB), size=  64MB, count=1: uncachable
```

```
0x00000000-0x7fffffff write-back
0x80000000-0xbfffffff write-back
0xc0000000-0xdfffffff write-back
	0xddc00000-0xddffffff uncachable
	0xde000000-0xdfffffff uncachable
0xe0000000-0xf0000000 write-combining
0x100000000-0x120000000 write-back
	0x11c000000-0x120000000 uncachable
```

Reg05 and Reg06 are only a guess.
Reg05 depends on the mapped in video area.
Reg06 depends on the memory size (>= 4GB) and layout of the system.

If you have less than 4GB installed, e.g. 2GB you probably won't need reg01 02 03 04 06 07.
Uncachable entries are only needed if these areas overlap cachable areas. Entries in /proc/mtrr need to be the power of 2.

---

### Post by conmat on 2010-02-15
Karmic 64-bit
Lenovo T400
8GB RAM
Using Intel graphics and Ubuntu drivers
(new to linux - I know just enough to be dangerous!)

I have the same error message

I get  this output:

foobar@foobar:~$ dmesg | grep drm
[    3.098710] [drm] Initialized drm 1.1.0 20060810
[    3.224941] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    3.225104] [drm] set up 31M of stolen space
[    3.481355] fb0: inteldrmfb frame buffer device
[    3.484759] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.826128] [drm] LVDS-8: set mode 1440x900 c
foobar@foobar:~$ cat /proc/mtrr
reg00: base=0x23c000000 ( 9152MB), size=   64MB, count=1: uncachable
reg01: base=0x0be000000 ( 3040MB), size=   32MB, count=1: uncachable
reg02: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg03: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg04: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg05: base=0x200000000 ( 8192MB), size= 1024MB, count=1: write-back
reg06: base=0x0bde00000 ( 3038MB), size=    2MB, count=1: uncachable
foobar@foobar:~$ cat /proc/iomem
00000000-00000fff : System RAM
00001000-00005fff : reserved
00006000-0009ebff : System RAM
0009ec00-0009ffff : reserved
000c0000-000c3fff : pnp 00:00
000c4000-000c7fff : pnp 00:00
000c8000-000cbfff : pnp 00:00
000cc000-000cffff : pnp 00:00
000d0000-000d3fff : pnp 00:00
000dc000-000fffff : reserved
00100000-bd4a0fff : System RAM
  01000000-0153ae1f : Kernel code
  0153ae20-0185b10f : Kernel data
  0191f000-01a2f783 : Kernel bss
bd4a1000-bd4a6fff : reserved
bd4a7000-bd5b6fff : System RAM
bd5b7000-bd60efff : reserved
bd60f000-bd6c5fff : System RAM
bd6c6000-bd6d0fff : ACPI Non-volatile Storage
bd6d1000-bd6d3fff : ACPI Tables
bd6d4000-bd6d7fff : reserved
bd6d8000-bd6dbfff : ACPI Non-volatile Storage
bd6dc000-bd6defff : reserved
bd6df000-bd705fff : ACPI Non-volatile Storage
bd706000-bd707fff : ACPI Tables
bd708000-bd90efff : reserved
bd90f000-bd99efff : ACPI Non-volatile Storage
bd99f000-bd9fefff : ACPI Tables
bd9ff000-bd9fffff : System RAM
bda00000-bdbfffff : RAM buffer
bdc00000-bfffffff : reserved
c0000000-c01fffff : PCI Bus 0000:02
c0200000-c03fffff : PCI Bus 0000:02
c0400000-c05fffff : PCI Bus 0000:03
c0600000-c0600fff : Intel Flush Page
c4000000-c7ffffff : PCI CardBus 0000:16
d0000000-dfffffff : 0000:00:02.0
e0000000-efffffff : reserved
  e0000000-efffffff : pnp 00:02
    e0000000-e3ffffff : PCI MMCONFIG 0 [00-3f]
f0000000-f3ffffff : PCI Bus 0000:15
  f0000000-f3ffffff : PCI CardBus 0000:16
f4000000-f40fffff : PCI Bus 0000:05
f4100000-f41fffff : PCI Bus 0000:0d
f4200000-f42fffff : 0000:00:02.1
f4300000-f43fffff : PCI Bus 0000:03
  f4300000-f4301fff : 0000:03:00.0
    f4300000-f4301fff : iwlagn
f4400000-f47fffff : 0000:00:02.0
f4800000-f7ffffff : PCI Bus 0000:15
  f4800000-f4800fff : 0000:15:00.0
    f4800000-f4800fff : yenta_socket
  f4801000-f48017ff : 0000:15:00.1
    f4801000-f48017ff : ohci1394
f8000000-f9ffffff : PCI Bus 0000:05
fa000000-fbffffff : PCI Bus 0000:0d
fc000000-fc01ffff : 0000:00:19.0
  fc000000-fc01ffff : e1000e
fc020000-fc023fff : 0000:00:1b.0
  fc020000-fc023fff : ICH HD audio
fc024000-fc024fff : 0000:00:03.3
fc025000-fc025fff : 0000:00:19.0
  fc025000-fc025fff : e1000e
fc226000-fc2267ff : 0000:00:1f.2
  fc226000-fc2267ff : ahci
fc226800-fc22680f : 0000:00:03.0
fc226c00-fc226fff : 0000:00:1a.7
  fc226c00-fc226fff : ehci_hcd
fc227000-fc2273ff : 0000:00:1d.7
  fc227000-fc2273ff : ehci_hcd
fc227400-fc2274ff : 0000:00:1f.3
fec00000-fec0ffff : reserved
  fec00000-fec00fff : IOAPIC 0
fed00000-fed003ff : HPET 0
  fed00000-fed003ff : reserved
fed10000-fed13fff : reserved
  fed10000-fed13fff : pnp 00:02
fed18000-fed19fff : reserved
  fed18000-fed18fff : pnp 00:02
  fed19000-fed19fff : pnp 00:02
fed1c000-fed8ffff : reserved
  fed1c000-fed1ffff : pnp 00:02
  fed45000-fed4bfff : pnp 00:02
fee00000-fee00fff : Local APIC
  fee00000-fee00fff : reserved
ff800000-ffffffff : reserved
100000000-23bffffff : System RAM

Any suggestions appreciated!!!

---

### Post by djolk on 2010-02-20
I have the same problem with /proc/mtrr and have yet to stumble upon the correct mtrr layout. I, too, would take suggestions.  I've tried both archlinux and ubuntu and have the same mtrr table.

here is /proc/mtrr


```
[djolk@tunamelt ~]$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size=32768MB, count=1: write-back
reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg02: base=0x0dde00000 ( 3550MB), size=    2MB, count=1: uncachable
reg03: base=0x0de000000 ( 3552MB), size=   32MB, count=1: uncachable

``````
00000000-00001fff : System RAM
00002000-00005fff : reserved
00006000-0009efff : System RAM
0009f000-0009ffff : reserved
000a0000-000bffff : Video RAM area
000c0000-000c7fff : Video ROM
000f0000-000fffff : System ROM
00100000-ddabf3ff : System RAM
  01000000-012bb149 : Kernel code
  012bb14a-013e39c7 : Kernel data
  0144e000-0152f023 : Kernel bss
ddabf400-ddcc13ff : ACPI Non-volatile Storage
ddcc1400-dfffffff : reserved
  ddd00000-dddfffff : pnp 00:0c
e0000000-efffffff : 0000:00:02.0
f0000000-f00fffff : PCI Bus 0000:09
  f0000000-f000ffff : 0000:09:00.0
    f0000000-f000ffff : r8169
  f0010000-f0010fff : 0000:09:00.0
    f0010000-f0010fff : r8169
  f0020000-f003ffff : 0000:09:00.0
f0100000-f03fffff : PCI Bus 0000:0d
f0400000-f05fffff : PCI Bus 0000:0b
f0600000-f07fffff : PCI Bus 0000:0b
f0800000-f09fffff : PCI Bus 0000:0c
f0a00000-f0a00fff : Intel Flush Page
f6600000-f67fffff : PCI Bus 0000:0d
f6800000-f68fffff : PCI Bus 0000:09
f6900000-f69fffff : PCI Bus 0000:0c
  f69f0000-f69fffff : 0000:0c:00.0
    f69f0000-f69fffff : ath9k
f6afbf00-f6afbfff : 0000:00:1f.3
f6afc000-f6afffff : 0000:00:1b.0
  f6afc000-f6afffff : ICH HD audio
f6b00000-f6bfffff : 0000:00:02.1
f6c00000-f6ffffff : 0000:00:02.0
f8000000-fbffffff : PCI MMCONFIG 0 [00-3f]
  f8000000-fbffffff : reserved
    f8000000-fbffffff : pnp 00:0c
fec00000-fec0ffff : reserved
  fec00000-fec00fff : IOAPIC 0
fed00000-fed003ff : HPET 0
  fed00000-fed003ff : pnp 00:09
fed18000-fed1bfff : reserved
  fed18000-fed1bfff : pnp 00:0c
fed1c000-fed1c3ff : 0000:00:1d.7
  fed1c000-fed1c3ff : ehci_hcd
fed1c400-fed1c7ff : 0000:00:1a.7
  fed1c400-fed1c7ff : ehci_hcd
fed1c800-fed1cfff : 0000:00:1f.2
  fed1c800-fed1cfff : pnp 00:0c
    fed1c800-fed1cfff : ahci
fed20000-fed8ffff : reserved
  fed20000-fed8ffff : pnp 00:0c
feda0000-feda5fff : reserved
  feda0000-feda3fff : pnp 00:0c
  feda4000-feda4fff : pnp 00:0c
  feda5000-feda5fff : pnp 00:0c
feda6000-feda6fff : pnp 00:0c
fee00000-fee0ffff : reserved
  fee00000-fee0ffff : pnp 00:0c
    fee00000-fee00fff : Local APIC
ff800000-ff8fffff : pnp 00:01
ffa00000-ffbfffff : pnp 00:0c
ffc00000-ffcfffff : pnp 00:01
ffe00000-ffffffff : reserved
  ffe00000-ffffffff : pnp 00:0c
```I've learned that you have to remove reg03, then reg02 then reg00, then reg01 and it doesn't crash... but as for what it SHOULD look like I am bit lost and not sure what iomen or lspci -vvnn is telling me.

---

### Post by djolk on 2010-02-20
My aplologies regarding the mtrr-uncover program. I've used it to create this script:

```
#!/bin/bash

#Remove existing mtrr entires.  Order matters!

echo "disable=3" >| /proc/mtrr
echo "disable=2" >| /proc/mtrr
echo "disable=0" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr

echo "base=0x000000000 size=0x080000000 type=write-back" >| /proc/mtrr 
echo "base=0x080000000 size=0x040000000 type=write-back" >| /proc/mtrr
echo "base=0x0c0000000 size=0x020000000 type=write-back" >| /proc/mtrr
echo "base=0x100000000 size=0x100000000 type=write-back" >| /proc/mtrr
echo "base=0x200000000 size=0x200000000 type=write-back" >| /proc/mtrr
echo "base=0x400000000 size=0x400000000 type=write-back" >| /proc/mtrr
echo "base=0xe0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
```

And now I have a much better looking /proc/mtrr:[djolk@tunamelt ~]$ cat /proc/mtrr
```
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  512MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size= 4096MB, count=1: write-back
reg04: base=0x200000000 ( 8192MB), size= 8192MB, count=1: write-back
reg05: base=0x400000000 (16384MB), size=16384MB, count=1: write-back
reg06: base=0x0e0000000 ( 3584MB), size=  256MB, count=1: write-combining

```

I am still not certain if this is exactly what /proc/mtrr should look like but my system is much more respsonsive.

---

### Post by Tobis87 on 2010-04-07
Conmat: I need the video area in which write-combining could be enabled. In order to calculate the Mtrrs.

djolk: Almost right. But you forgot to include the uncachable regions and you don't need cover the full 32gb ram, because your highest Systen-Ram is:

00100000-ddabf3ff : System RAM

```
#!/bin/bash

echo "disable=3" >| /proc/mtrr
echo "disable=2" >| /proc/mtrr
echo "disable=0" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr

echo "base=0x00000000 size=0x80000000 type=write-back" >| /proc/mtrr
echo "base=0x80000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=0xc0000000 size=0x20000000 type=write-back" >| /proc/mtrr
echo "base=0xdde00000 size=0x200000 type=uncachable" >| /proc/mtrr
echo "base=0xde000000 size=0x2000000 type=uncachable" >| /proc/mtrr
echo "base=0xe0000000 size=0x10000000 type=write-combining" >| /proc/mtrr
```

```
0x00000000-0x7fffffff write-back
0x80000000-0xbfffffff write-back
0xc0000000-0xdfffffff write-back
	0xdde00000-0xddffffff uncachable
	0xde000000-0xdfffffff uncachable
0xe0000000-0xf0000000 write-combining
```

---

### Post by Pavlo Solntsev on 2010-11-14
Hi, Could you help me figure out parameters appropriate for my system.
Laptop ASUS with Ubuntu 10.10. 86x_64, Video: gm45, RAM 4Gb
Script above gave me 
base=0xd0000000 size=0x10000000 type=write-combining
My current /proc/mtrr has:

reg00: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg01: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg03: base=0x0bde00000 ( 3038MB), size=    2MB, count=1: uncachable
reg04: base=0x0be000000 ( 3040MB), size=   32MB, count=1: uncachable

$lspci -v # VGA part
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1862
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at dc00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

Thank you very much for you help.

---

### Post by FerroPower on 2011-09-30
Sorry for posting in old thread but I am also using GM45 intel card(Dell 1545). I am also getting the following mtrr error Please Help !!!


mahesh@togo:~$ dmesg | grep drm
[    1.038472] [drm] Initialized drm 1.1.0 20060810
[    1.139225] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    1.139670] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.139672] [drm] Driver supports precise vblank timestamp query.
[    1.606442] fbcon: inteldrmfb (fb0) is primary device
[    1.647565] fb0: inteldrmfb frame buffer device
[    1.647567] drm: registered panic notifier
[    1.663852] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0

---

