---
title: "Suspend wakes up immediatelly"
date: 2010-11-03
forum: Hardware
---

### Post by maddis on 2010-11-03
I found [this]("http://ubuntuforums.org/showthread.php?t=505890") old thread describing the exact same problem I'm having now. Problem is though that the thread is quite old so kernel has changed quite a bit since then and the thread never says how the problem was resolved. If it ever was.

I'm running Ubuntu 10.04 LTS on Atom based hardware. Suspend seems to work fine except the system wakes up right away when I put it in suspend. 

Here is short log what happens:
```

[ 2572.342816] PM: Syncing filesystems ... done.
[ 2572.350957] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2572.359823] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 2572.367274] Suspending console(s) (use no_console_suspend to debug)
[ 2572.400324] sd 0:0:0:0: [sda] Stopping disk
[ 2572.401427] e1000e 0000:05:00.0: PCI INT A disabled
[ 2572.401441] e1000e 0000:05:00.0: PME# enabled
[ 2572.412434] e1000e 0000:01:00.0: PCI INT A disabled
[ 2572.412447] e1000e 0000:01:00.0: PME# enabled
[ 2572.423236] sdhci-pci 0000:00:1e.0: PCI INT A disabled
[ 2572.423273] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[ 2572.423285] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 2572.423295] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 2572.423304] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 2572.524406] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 2572.535314] PM: suspend devices took 0.162 seconds
[ 2572.535944] ehci_hcd 0000:00:1d.7: PME# disabled
[ 2572.546518] ACPI: Preparing to enter system sleep state S3
[ 2572.548103] Disabling non-boot CPUs ...
[ 2572.549255] Breaking affinity for irq 9
[ 2572.549255] Breaking affinity for irq 16
[ 2572.549255] Breaking affinity for irq 18
[ 2572.550554] CPU 1 is now offline
[ 2572.550561] SMP alternatives: switching to UP code
[ 2572.556833] CPU1 is down
[ 2572.556911] Extended CMOS year: 2000
[ 2572.556911] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 2572.556911] Extended CMOS year: 2000
[ 2572.557055] Enabling non-boot CPUs ...
[ 2572.557955] SMP alternatives: switching to SMP code
[ 2572.562182] Booting processor 1 APIC 0x1 ip 0x6000
[ 2572.555232] Initializing CPU#1
[ 2572.555232] Calibrating delay using timer specific routine.. 3199.78 BogoMIPS (lpj=1599894)

```

Have anyone else had similar problems and how did you solve it? I've tried to configure suspend with kernel command line options, but I'm starting to think that it's not going to be enough.

---

