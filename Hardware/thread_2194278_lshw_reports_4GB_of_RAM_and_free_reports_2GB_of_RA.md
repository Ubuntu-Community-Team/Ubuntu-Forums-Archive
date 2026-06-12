---
title: "lshw reports 4GB of RAM and free reports 2GB of RAM"
date: 2013-12-17
forum: Hardware
---

### Post by benjamin.a.schultz on 2013-12-17
I have a lenovo t440 with 1 stick of 4GB of RAM installed. I am running 64 bit Ubuntu 13.10.



When I check how much RAM I have using free, it reports that 1.9GB is available

benjib0t@benjib0t-ThinkPad-T440:~/glotzer/worklog$ free -m
             total       used       free     shared    buffers     cached
Mem:          1953       1741        211          0         17        737
-/+ buffers/cache:        986        966
Swap:         2063        491       1572 

However, the BIOS and lshw 4 GB

benjib0t@benjib0t-ThinkPad-T440:~/glotzer/worklog$ sudo lshw -c memory
[sudo] password for benjib0t: 
  *-memory
       description: System Memory
       physical id: 5
       slot: System board or motherboard
       size: 4GiB
     *-bank
          description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
          product: M471B5173QH0-YK0
          vendor: Samsung
          physical id: 0
          serial: 14474F71
          slot: ChannelB-DIMM0
          size: 4GiB
          width: 8 bits
          clock: 1600MHz (0.6ns)
  *-firmware
       description: BIOS
       vendor: LENOVO
       physical id: 3a
       version: GJET64WW (2.14 )
       date: 11/12/2013
       size: 128KiB
       capacity: 15MiB
       capabilities: pci pnp upgrade shadowing cdboot bootselect acpi usb biosbootspecification uefi

Interestingly, if I run lshw without root privleges, it gives the same answer at 'free"
benjib0t@benjib0t-ThinkPad-T440:~/glotzer/worklog$ lshw -c memory
WARNING: you should run this program as super-user.
  *-memory                
       description: System memory
       physical id: 0
       size: 1953MiB
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

 I  have seen on forums that sometimes integrated graphic cards will nab a  chunk of the system memory, and that this is typically adjustable from  within the BIOS. I dug around in the BIOS to try to find such a setting,  and could not locate one.

Does anyone know what could be causing this discrepancy?

Thanks in advance for any help.

---

### Post by benjamin.a.schultz on 2013-12-17
[This post]("http://ubuntuforums.org/showthread.php?t=2100207&page=5") describes a similar problem from 2 years ago, which was eventually solved with a BIOS upgrade. I am running version 2.14 of the T440 BIOS, which is the most recent version.

---

### Post by benjamin.a.schultz on 2013-12-18
I had ordered a 8 GB stick of ram and installed it today. Now I see 6 GB with free, and all 8 with lshw. To me this indicates that somewhere, something is setting aside 2GB for itself...?

benjib0t@benjib0t-ThinkPad-T440:~$ sudo lshw -c memory
*-memory
       description: System Memory
       physical id: 5
       slot: System board or motherboard
       size: 8GiB
     *-bank
          description: Chip DDR3 Synchronous 1600 MHz (0.6 ns)
          product: 16KTS1G64HZ-1G6E1
          vendor: Micron
          physical id: 0
          serial: &#33987;&#65533;
          slot: ChannelB-DIMM0
          size: 8GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)


benjib0t@benjib0t-ThinkPad-T440:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5985        775       5209          0         40        403
-/+ buffers/cache:        331       5654
Swap:         2063          0       2063

---

### Post by philinux on 2013-12-18
From here [https://communities.intel.com/thread/43739](https://communities.intel.com/thread/43739) it says no dedicated memory and 1745mb shared. So thats where 2 gig or so is going.

[http://en.wikipedia.org/wiki/Shared_graphics_memory](http://en.wikipedia.org/wiki/Shared_graphics_memory)

---

### Post by benjamin.a.schultz on 2013-12-18
Thanks for the reply philinux! I see the post in the intel forum, saying that the card takes 1745mb shared mem. When I check I my machine it says that graphics card gets 256 + 4 MB.

benjib0t@benjib0t-ThinkPad-T440:~$ sudo lspci -vv
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 220c
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 62
    Region 0: Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Address: fee0f00c  Data: 4152
    Capabilities: [d0] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [a4] PCI Advanced Features
        AFCap: TP+ FLR+
        AFCtrl: FLR-
        AFStatus: TP-
    Kernel driver in use: i915


Could the information reported by lspci be incorrect?

---

### Post by philinux on 2013-12-18
Not incorrect, [http://askubuntu.com/questions/309626/how-to-check-what-type-my-video-card-is-and-its-memory-size](http://askubuntu.com/questions/309626/how-to-check-what-type-my-video-card-is-and-its-memory-size)

---

### Post by benjamin.a.schultz on 2013-12-18
I also tallied up the memory allocated devices reported by lshw to see if there were other allocations hiding and I got a total of 262 MB

benjib0t@benjib0t-ThinkPad-T440:~$ sudo lshw  | grep  resources
             resources: irq:62 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:4000(size=64)
             resources: irq:59 memory:f0630000-f0633fff
             resources: irq:61 memory:f0620000-f062ffff
             resources: irq:60 memory:f0639000-f063901f
             resources: irq:56 memory:f0600000-f061ffff memory:f063e000-f063efff ioport:4080(size=32)
             resources: irq:63 memory:f0634000-f0637fff
             resources: irq:17 memory:f0500000-f05fffff
                resources: irq:58 memory:f0500000-f0500fff
             resources: irq:18 ioport:3000(size=4096) memory:f0400000-f04fffff
                resources: ioport:3000(size=256) memory:f0400000-f0403fff
             resources: irq:23 memory:f063d000-f063d3ff
             resources: irq:0
             resources: irq:57 ioport:40a8(size=8) ioport:40b4(size=4) ioport:40a0(size=8) ioport:40b0(size=4) ioport:4060(size=32) memory:f063c000-f063c7ff
             resources: memory:f0638000-f06380ff ioport:efa0(size=32)

---

### Post by benjamin.a.schultz on 2013-12-18
Reading this comment: 
>      Well, this is a little bit tricky. Intel  graphics do not have dedicated memory but utilizes some of the  computer's system memory. The amount of memory used for graphics may be a  fixed amount or may vary up to a maximum amount. It depends on if your  computer manufacturer has configured your computer to use a fixed  amount, a dynamic amount (varying up to a maximum amount), or a  combination of both fixed and dynamic amounts of graphics memory.     &#8211;          [Frantique]("http://askubuntu.com/users/68484/frantique")     [Jun 18 at 13:31]("http://askubuntu.com/questions/309626/how-to-check-what-type-my-video-card-is-and-its-memory-size#comment390474_309630")                 



and this FAQ: [http://www.intel.com/support/graphics/sb/CS-033984.htm](http://www.intel.com/support/graphics/sb/CS-033984.htm)



I tried checking memory from an Unbuntu 12.04.3  and Fedora live boot disk, and it still shows 6GB, rather than 8 GB of memory.

I am left wondering if somehow the graphics card all of its maximum 1792 MB even though the OS says it's only dedicated 260MB for it.

---

