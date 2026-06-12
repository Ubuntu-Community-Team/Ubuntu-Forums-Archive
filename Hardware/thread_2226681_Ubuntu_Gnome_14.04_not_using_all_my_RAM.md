---
title: "Ubuntu Gnome 14.04 not using all my RAM"
date: 2014-05-28
forum: Hardware
---

### Post by lambdafox on 2014-05-28
My motherboard is a Tyan S2877.

The BIOS is flashed to the latest:  v1.07

The BIOS correctly counts the RAM.  Ubuntu GNOME 14.04 (amd64) only sees 3GB of RAM???

BIOS Settings

Under Main:

Installed OS:  see [COLOR=#b22222]Note 1[/COLOR] below

Under Advanced - Hammer,

ECC: Enabled
ECC Scrub Redir:  Disabled
DRAM ECC Scrub Ctl:  Disabled
Mem Clock Value:  200
Mode Memory Interleave: See [COLOR=#800080]Note 2[/COLOR] below
DRAM Bank Interleave: Disabled
4GB Memory Hole Adjust:  Auto
DDR Clock Jitter: Enabled
Memhole Mapping:  Disabled (Other choices are Software or Hardware)
Enable all memory clocks: Populated
Controller Config Mode: Auto
Timeing Config Mode:  Auto
Swizzle memory banks: Disabled
Large Memory Simulation: Disabled
MTRR Mapping:  Continuous


Under Memory

Cach RAM is set to 1024 k
Memory Cache is Enabled
System BIOS:  uncached
Video BIOS:  uncached
Base 0-512k:  uncached
Base 512k 64k:  uncached
Extended Memory Area:  uncached

All caches listed after this are disabled.

[COLOR=#b22222]Note 1:[/COLOR] Changing the installed OS on the BIOS mainscreen to Other, Linux or Windows XP 64 does not change the following problem.  (There is a Win XP Pro setting, but I have not tried it since that is a 32 bit os w a 3GB limit...)

After googling and searching the forum, I thought maybe it was a problem with the kernel not being numa enabled.  Here is what I get when I run numactl --hardware in terminal:

[COLOR=#800080]Note 2:[/COLOR]  I have done this with the numa on and off and get the same results as you can see here.

Working with 4x1GB sticks of RAM

All 4 in the CPU 0 memory slots with numa off

available: 1 nodes (0)
node 0 cpus: 0 1 2 3
node 0 size: 3008 MB
node 0 free: 2355 MB
node distances:
node   0 
  0:  10 

two sticks for each cpu with numa on

available: 2 nodes (0-1)
node 0 cpus: 0 1
node 0 size: 2001 MB
node 0 free: 1731 MB
node 1 cpus: 2 3
node 1 size: 1006 MB
node 1 free: 666 MB
node distances:
node   0   1 
  0:  10  20 
  1:  20  10 

two sticks for each cpu with numa off

available: 1 nodes (0)
node 0 cpus: 0 1 2 3
node 0 size: 3008 MB
node 0 free: 2395 MB
node distances:
node   0 
  0:  10

---

### Post by lambdafox on 2014-05-29
> **lambdafox said:**
> ... Memhole Mapping:  Disabled (Other choices are Software or Hardware) ...

This was the culprit.

*Disabled* caps memory at 3GB

Depending on which specific processor you have, this needs to be set to *Software* (earlier processors) or *Hardware* (later processors).

---

