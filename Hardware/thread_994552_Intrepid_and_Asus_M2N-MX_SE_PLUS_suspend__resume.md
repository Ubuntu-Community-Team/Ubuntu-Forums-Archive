---
title: "Intrepid and Asus M2N-MX SE PLUS suspend / resume"
date: 2008-11-26
forum: Hardware
---

### Post by cadeon on 2008-11-26
I love me some Ubuntu. Intrepid is some really good stuff.

The ONLY problem I've had with my install so far is suspending. The machine seems to suspend just fine, but immediately wakes back up. Same deal with hibernating- it hibernates just fine, but instead of shutting off, immediately reboots (and correctly resumes from the hibernate).

I have:

ASUS M2N-MX SE PLUS
Athlon X2 4600+
PCI Express GeForce 7100

Any ideas? Thanks

---

### Post by Murz on 2009-03-10
I have the same problem with Asus M2N-MX SE PLUS (using internal video) and Ubuntu 8.10. Updating bios to latest version (0602) didn't solve this problem.

---

### Post by mecrip on 2009-04-25
Same for me with an ASUS F3JA... 

from dmesg i can't see nothing strange:

```

[ 1444.032178] PM: suspend devices took 3.160 seconds
[ 1444.032641] ACPI: Preparing to enter system sleep state S3
[ 1444.040907] Disabling non-boot CPUs ...
[ 1444.144023] CPU 1 is now offline
[ 1444.144027] SMP alternatives: switching to UP code
[ 1444.335195] CPU0 attaching NULL sched-domain.
[ 1444.335199] CPU1 attaching NULL sched-domain.
[ 1444.335488] CPU0 attaching NULL sched-domain.
[ 1444.335667] CPU1 is down
[ 1444.335667] Back to C!
[ 1444.335667] Force enabled HPET at resume
[ 1444.335667] Enabling non-boot CPUs ...
[ 1444.336092] SMP alternatives: switching to SMP code
[ 1444.527959] Booting processor 1 APIC 0x1 ip 0x6000
[ 1444.335042] Initializing CPU#1
[ 1444.335042] Calibrating delay using timer specific routine.. 3323.41 BogoMIPS (lpj=6646828)
[ 1444.335042] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 1444.335042] CPU: L2 cache: 2048K
[ 1444.335042] CPU: Physical Processor ID: 0
[ 1444.335042] CPU: Processor Core ID: 1


```

---

