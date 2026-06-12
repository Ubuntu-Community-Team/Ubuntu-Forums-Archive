---
title: "How FGLRX extracts VGABIOS if I get input/output error? AMD magic?"
date: 2017-06-29
forum: Hardware
---

### Post by mward2015 on 2017-06-29
Laptop has integrated+discrete 2 AMD GPUs and I need to get their VGABIOS. People do this: ```
echo 1 > /sys/devices/pci0000\:00/0000\:00\:01.0/rom
cat /sys/devices/pci0000\:00/0000\:00\:01.0/rom > vgabios.bin
``` But it works only for integrated GPU! While trying the same approach for discrete: ```
cat: /sys/devices/pci0000\:00/0000\:00\:02.0/0000\:01\:00.0/rom: Input/output error
``` I/O error happens regardless of what GPU is active. I tried looking at `/proc/iomem`, there's
just one Video ROM at `000c0000-000cf1ff` - for integrated GPU, but I already got it and need for discrete

Impossible to extract discrete VGABIOS from my hardware under Linux?
Wrong! ;) `Radeon Control Center` aka `fglrx-amdcccle` shows this: ```
Hardware: AMD Radeon R5 M230 Series
        BIOS Date - 11/28/13,01:19:25
        BIOS Version - 015.041.000.000.045149
        BIOS Part Number - BR45149.002
``` This info is a part of any AMD's VGABIOS at its' beginning. If `amdcccle` was able to access VGABIOS to
get this info, root also can do it - and extract the rest of VGABIOS as well! **But how?**

**Plan A:** use `ltrace` to record amdcccle's activity during its' launch and find out what it is doing to access VGABIOS.
Its doing so much things that `ltrace` crashes with `call nesting too deep`. I could rebuild `ltrace` to remove this stupid limitation from `handle_event.c` : ```
if (proc->callstack_depth == MAX_CALLDEPTH - 1) {
        fprintf(stderr, "%s: Error: call nesting too deep!\n", __func__);
        abort();
        return;
    }
``` However this log might be too huge and difficult to understand, so I am researching other plans:

**Plan B:** after amdcccle has been launched, run a simple C mmap'ing program with root rights to dump the whole 16 GB of physical memory,
then search through this dump for values like `45149 (BIOS Part Number)`  - in hope that amdcccle doesn't stop after reading the very beginning,
reads the whole VGABIOS and keeps it somewhere in RAM instead of instantly free'ing after the info extraction

**Plan C:** analyze Linux logs - which logs in particular? I found some interesting lines at XOrg's log: ```
[    18.751] (--) PCI:*(0:0:1:0) 1002:990b:17aa:3804 rev 0, Mem @ 0xd0000000/268435456, 0xf0200000/262144, I/O @ 0x00004000/256
    [    18.751] (--) PCI: (0:1:0:0) 1002:6665:17aa:3804 rev 0, Mem @ 0xe0000000/268435456, 0xf0100000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
    ...
    [    19.393] (--) fglrx(0): Chipset: "AMD Radeon R5 M230 Series" (Chipset = 0x6665)
    [    19.393] (--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x3804)
    [    19.393] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
    [    19.393] (--) fglrx(0): MMIO registers at 0xf0100000
    [    19.393] (--) fglrx(0): I/O port at 0x00003000
    [    19.393] (==) fglrx(0): ROM-BIOS at 0x000c0000
    [    19.419] (II) fglrx(0): ATIF platform detected
    [    19.420] (II) fglrx(0): AC Adapter is used
    [    19.427] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
``` But at 0x000c0000 there is integrated VGABIOS, not discrete. Wrong info?

**Please comment my ideas and offer your own plans!**[I]
(just should not involve using Windows or extracting from vendor's BIOS, I want to do it by using Linux capabilities)[/I]

--------------------
`lspci -tv`:

    ```
-[0000:00]-+-00.0  [AMD] Family 15h (Models 10h-1fh) Root Complex [1022:1410]
               +-01.0  [AMD/ATI] Richland [Radeon HD 8650G] [1002:990b]
               +-01.1  [AMD/ATI] Trinity HDMI Audio Controller [1002:9902]
               +-02.0-[01]----00.0 [AMD/ATI] Jet PRO [Radeon R5 M230] [1002:6665]
               ...
``` `lspci` is a bit different: ```

    00:01.0 VGA compatible controller [0300]: [AMD/ATI] Richland [Radeon HD 8650G]
    01:00.0 Display controller [0380]: [AMD/ATI] Jet PRO [Radeon R5 M230]
```

Shortened `lspci -vv`: ```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8650G] (prog-if 00 [VGA controller])
        Subsystem: Lenovo Device 3804
        Interrupt: pin A routed to IRQ 32
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Region 1: I/O ports at 4000 [size=256]
        Region 2: Memory at f0200000 (32-bit, non-prefetchable) [size=256K]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [58] Express (v2) Root Complex Integrated Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Address: 00000000fee0f00c  Data: 4192
        Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Kernel driver in use: fglrx_pci
```


    ```
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Jet PRO [Radeon R5 M230]
        Subsystem: Lenovo Device 3804
        Interrupt: pin A routed to IRQ 33
        Region 0: Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Region 2: Memory at f0100000 (64-bit, non-prefetchable) [size=256K]
        Region 4: I/O ports at 3000 [size=256]
        [virtual] Expansion ROM at f0140000 [disabled] [size=128K]
        Capabilities: [48] Vendor Specific Information: Len=08 <?>
        Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
            Address: 00000000fee0f00c  Data: 41a2
        Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [150 v2] Advanced Error Reporting
        Capabilities: [270 v1] #19
        Kernel driver in use: fglrx_pci
```

---

### Post by QIII on 2017-06-29
What release of Ubuntu are you using?

Since fglrx only works with two supported releases, 14.04 and 14.04.1, there is only a very narrow slice of the Ubuntu community for whom this is an issue.

---

### Post by mward2015 on 2017-06-30
> **QIII said:**
> What release of Ubuntu are you using?

Since fglrx only works with two supported releases, 14.04 and 14.04.1, there is only a very narrow slice of the Ubuntu community for whom this is an issue.

Actually fglrx is compatible up to 14.04.4 *(14.04.5 update breaks it, so the people who upgraded to 14.04.5 had to downgrade their kernel and HWE stack) *
I have tested both 14.04.1 and 14.04.4 - they have exactly the same problem that is described above

Do you know any possible solution for it?

---

### Post by gsahli on 2017-06-30
> **mward2015 said:**
> 
Do you know any possible solution for it?

Try 16.04.2. A lot of AMD APU issues have been cleared up with new versions of radeon (module/driver) or amdgpu (driver), and mesa. 
PS - I was just thinking of "making use" of your two graphics adapters - not extracting video BIOS.

---

### Post by QIII on 2017-06-30
Derp.  Right you are.  I'm the one one who made the bug report for 14.04.2.  The break I was thinking of was post 12.04.1.

OK, anyway...

What AMD exposes of its VGABIOS to Linux detection may be variable, although I don't think that would be likely.  When I get home I'll see what I can get for my R9 380X on 16.04.2 -- no fglrx, of course.  If I can get something it might indicate that a newer kernel provides the functionality.

---

### Post by mward2015 on 2017-06-30
> **gsahli said:**
> Try 16.04.2. A lot of AMD APU issues have been cleared up with new versions of radeon (module/driver) or amdgpu (driver), and mesa. 
PS - I was just thinking of "making use" of your two graphics adapters - not extracting video BIOS. My discrete GPU (R5 M230) is from Southern Islands family - GCN 1.1,
open source support for early GCN architectures is still experimental
and I am getting exactly the same bug as this person - Fatal error during GPU init :
[https://bugs.freedesktop.org/show_bug.cgi?id=101473](https://bugs.freedesktop.org/show_bug.cgi?id=101473)
That's why I am still staying at 14.04.4 despite its too old already

---

### Post by mward2015 on 2017-06-30
> **QIII said:**
> What AMD exposes of its VGABIOS to Linux detection may be variable, although I don't think that would be likely.  When I get home I'll see what I can get for my R9 380X on 16.04.2 -- no fglrx, of course.  If I can get something it might indicate that a newer kernel provides the functionality If AMD proprietary software is somehow accessing VGABIOS to get this info, maybe through some undocumented secret "backdoor way", Linux should be able to do the same thing as well - just need to reverse engineer or ask AMD. I already e-mail'ed AMD but don't know if they are ready to disclose their fglrx secrets :P

You may have better luck for VGABIOS extraction because your GPU is from recent AMD family *(not early GCC, open source for my card is still very bad)* - and also you got a desktop computer, things are a bit easier there. Do you have any AMD laptop with similar hardware? In any case, curious to learn your results

---

