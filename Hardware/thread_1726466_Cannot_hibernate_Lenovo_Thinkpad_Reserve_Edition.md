---
title: "Cannot hibernate Lenovo Thinkpad Reserve Edition"
date: 2011-04-11
forum: Hardware
---

### Post by keithbannister on 2011-04-11
Hi,

I've got a Lenovo Thinkpad Reserve Edition with Ubuntu 10.10. Everything updated.
I'm pretty sure there's enough swap.
When I try to hibernate using the gnome 'switch' control on the top right. The screen goes to black screen, thinks a bit then resumes immediately. 

Suspend works.

The second time I try, the black screen says:
"PM: Not enough free swap"


Ubuntu installed with wubi, which didn't have enough swap space. I had to add swap with swapon.

$ swapon -sf
Filename				Type		Size	Used	Priority
/host/ubuntu/disks/swap.disk            file		261116	1988	-1
/host/ubuntu/disks/swap2.disk           file		2097148	0	-2

My feeling the 'Not enough free swap' error is a phoney. I'm pretty sure there's enough free swap now, but I'm not sure which numbers to use here: 

$ cat /proc/meminfo 
MemTotal:        2019140 kB
MemFree:          889580 kB
Buffers:          390056 kB
Cached:           442720 kB
SwapCached:         1988 kB
Active:           333808 kB
Inactive:         724304 kB
Active(anon):     222816 kB
Inactive(anon):    32444 kB
Active(file):     110992 kB
Inactive(file):   691860 kB
Unevictable:        1116 kB
Mlocked:              32 kB
HighTotal:       1145544 kB
HighFree:         463684 kB
LowTotal:         873596 kB
LowFree:          425896 kB
SwapTotal:       2358264 kB
SwapFree:        2356276 kB
Dirty:               436 kB
Writeback:             0 kB
AnonPages:        224700 kB
Mapped:            78532 kB
Shmem:             28840 kB
Slab:              28840 kB
SReclaimable:      15404 kB
SUnreclaim:        13436 kB
KernelStack:        2512 kB
PageTables:         5520 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3367832 kB
Committed_AS:    1110656 kB
VmallocTotal:     122880 kB
VmallocUsed:       31940 kB
VmallocChunk:      50300 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       16376 kB
DirectMap4M:      892928 kB




Here's a suspicious section of /var/log/messages during an attempted hibernate:


Apr 11 21:24:40 ubuntu kernel: [ 1222.023064] Initializing CPU#1
Apr 11 21:24:40 ubuntu kernel: [ 1222.136521] ACPI Exception: AE_BAD_PARAMETER, Returned by Handler for [EmbeddedControl] (20100428/evregion-474)
Apr 11 21:24:40 ubuntu kernel: [ 1222.136530] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.LPMD] (Node f7023270), AE_BAD_PARAMETER
Apr 11 21:24:40 ubuntu kernel: [ 1222.136580] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU0._PPC] (Node f702ff18), AE_BAD_PARAMETER
Apr 11 21:24:40 ubuntu kernel: [ 1222.136627] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PPC] (Node f70b62d0), AE_BAD_PARAMETER
Apr 11 21:24:40 ubuntu kernel: [ 1222.136677] ACPI Exception: AE_BAD_PARAMETER, Evaluating _PPC (20100428/processor_perflib-144)
Apr 11 21:24:40 ubuntu kernel: [ 1222.136715] CPU1 is up
Apr 11 21:24:40 ubuntu kernel: [ 1222.137585] ACPI: Waking up from system sleep state S4

Attached: Full /var/log/messages

Attached: output of acpidump

---

