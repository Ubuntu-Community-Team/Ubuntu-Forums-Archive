---
title: "intel 915 GAV support"
date: 2005-09-06
forum: Hardware &amp; Laptops
---

### Post by mailmaldi on 2005-09-06
hi, 

i am using a intel 915GAV motherboard with p4 3.0Ghz HT proc,Seagate 80GB SATA

i installed ubuntu 5.04...my display is up...
i changed xorg.conf to meet my monitor specs...
so display is generally fine...except it doesnt seem to be optmized...

also theres no sound...

i downloaded the add-on cd (which btw is amazing..thanks jiyyo) & installed it...but still theres no sound on my system....FC3 didnt recognize my soundcard either...FC4 sound was crackling...

also the video placyback ( even off hdd ) is a bit choppy & mplayer doesnt play my divx at all...xine plays but is choppy..

could someone please direct me in the proper direction??

this is the output of lspci -v 
also y are my subsytems Unknown???
will this cause decrease in my systems performance???


```

root@maldi:~ # lspci -v
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev  04)
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] #09 [2109]

0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04) (p rog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: ffa00000-ffafffff
        Prefetchable memory behind bridge: cff00000-cfffffff
        Capabilities: [88] #0d [0000]
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable -
        Capabilities: [a0] #10 [0141]

0000:00:02.0 VGA compatible controller: Intel Corp. 82915G Express Chipset Famil y Graphics Controller (rev 04) (prog-if 00 [VGA])
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at ff480000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ec00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at ff440000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [d0] Power Management version 2

0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definiti on Audio Controller (rev 03)
        Subsystem: Intel Corp.: Unknown device e203
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at ff43c000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable -
        Capabilities: [70] #10 [0091]

0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: ff600000-ff6fffff
        Prefetchable memory behind bridge: 00000000cfb00000-00000000cfb00000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable -
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: ff700000-ff7fffff
        Prefetchable memory behind bridge: 00000000cfc00000-00000000cfc00000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable -
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: ff800000-ff8fffff
        Prefetchable memory behind bridge: 00000000cfd00000-00000000cfd00000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable -
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Exp ress Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: ff900000-ff9fffff
        Prefetchable memory behind bridge: 00000000cfe00000-00000000cfe00000
        Capabilities: [40] #10 [0141]
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable -
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at c800 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at cc00 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at d000 [size=32]

0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at d400 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at ff43bc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [20a0]

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3) (prog-if 01 [Subt ractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ff500000-ff5fffff
        Prefetchable memory behind bridge: 00000000cfa00000-00000000cfa00000
        Capabilities: [50] #0d [0000]

0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridg e (rev 03)
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at e800 [size=8]
        I/O ports at e400 [size=4]
        I/O ports at e000 [size=8]
        I/O ports at dc00 [size=4]
        I/O ports at d800 [size=16]
        Capabilities: [70] Power Management version 2

0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 03)
        Subsystem: Intel Corp.: Unknown device 4156
        Flags: medium devsel, IRQ 10
        I/O ports at c400 [size=32]

0000:06:08.0 Ethernet controller: Intel Corp.: Unknown device 1064 (rev 01)
        Subsystem: Intel Corp.: Unknown device 3057
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at ff500000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at bc00 [size=64]
        Capabilities: [dc] Power Management version 2


```

---

