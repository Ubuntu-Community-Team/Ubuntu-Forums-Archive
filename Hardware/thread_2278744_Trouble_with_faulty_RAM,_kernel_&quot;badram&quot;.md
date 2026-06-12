---
title: "Trouble with faulty RAM, kernel &quot;badram&quot; parameter not effective on 64-bit flavour"
date: 2015-05-18
forum: Hardware
---

### Post by UCyborg on 2015-05-18
Hi!

Some time ago, one of my memory modules has gone bad. I have 2x2 GB of RAM, the second stick seems to have a small defective region. Memtest86 reports faulty address as 00133a9feec, error bits is 00000800, switching reporting mode to the one that shows BadRAM patterns gives:

badram=0xb3a9feec,0xfffffffc

Using 32-bit version of Ubuntu, editing /boot/grub/grub.cfg to have GRUB_BADRAM="0xb3a9feec,0xfffffffc", sudo update-grub, reboot and my computer works without suddenly hanging, which is what happens after few minutes of usage otherwise. Not using GRUB_BADRAM and just appending badram=0xb3a9feec,0xfffffffc to kernel command-line also works.

64-bit version of Ubuntu is entirely different story. First of, documentation says BadRAM pattern should be extended to 64-bits for x64 kernel, so in my case:

GRUB_BADRAM="0x0000b3a9feec,0xfffffffffffc"

However, changing it like this just makes the computer hang before it even reaches the Grub screen. So I tried just appending badram parameter to kernel command-line (extending it to 64-bits ofcourse), but it doesn't work as it should neither. Machine successfully boots, "free" command reports 4 KB of less memory, but apparently it doesn't blacklist the actual defective sectors of RAM, but some good ones I guess, judging from the fact that computer once again just hangs after few minutes.

Any idea why it behaves like this on x64 kernel? Maybe the address and mask in the badram parameter should be different for x64? A bug in kernel? Maybe it should be reported on kernel bug tracker. I'm a bit pessimistic about getting support regarding this issue since there aren't a lot of people out there running their PCs with faulty RAM modules.

I have to add that I've tested this extensively and results are consistent:

x86 kernel - PC works 100% reliably IF BadRAM patch is applied, otherwise hangs after few minutes of usage.
x64 kernel - PC hangs after few minutes of usage, regardless of the BadRAM patch, applied or not, same results.

Any help regarding this issue would be appreciated.

---

### Post by tgalati4 on 2015-05-18
Perhaps 64-bit RAM requires a different address with padded bits.  Or, try adding one or two more zeros.  Try running memtest in 64-bit and see what the badram address is.

In 32-bit mode post the output of:

```
cat /proc/iomem
```

My quick research shows references back in 2001, so it is possible that a working 64-bit patch was never released or tested.

[https://help.ubuntu.com/community/BadRAM](https://help.ubuntu.com/community/BadRAM)

---

### Post by UCyborg on 2015-05-19
The address is 100% correct, both Memtest86 bundled with Ubuntu and Memtest86+ 5.01 report the same. 5.01 also indicates running in x64 mode. I could also use these exact information to make Windows happy and not constantly crash with a blue screen. Here's the content of /proc/iomem:

```
00000000-00000fff : reserved
00001000-0009d7ff : System RAM
0009d800-0009ffff : reserved
000a0000-000bffff : PCI Bus 0000:00
  000a0000-000bffff : Video RAM area
000c0000-000ce9ff : Video ROM
000d0000-000dffff : PCI Bus 0000:00
  000d0000-000d3fff : pnp 00:01
  000d4000-000d7fff : pnp 00:01
  000de000-000dffff : pnp 00:01
000e3000-000fffff : reserved
  000f0000-000fffff : System ROM
00100000-b3a9fbff : System RAM
  01000000-016f16b5 : Kernel code
  016f16b6-01a9177f : Kernel data
  01b79000-01c3ffff : Kernel bss
b3a9fc00-b3a9ffff : RAM buffer
b3aa0000-c7f9ffff : System RAM
c7fa0000-c7fadfff : ACPI Tables
c7fae000-c7fdffff : ACPI Non-volatile Storage
c7fe0000-c7fedfff : reserved
c7fee000-c7feffff : RAM buffer
c7ff0000-c7ffffff : reserved
c8000000-dfffffff : PCI Bus 0000:00
  ce000000-dfffffff : PCI Bus 0000:02
    ce000000-cfffffff : 0000:02:00.0
    d0000000-dfffffff : 0000:02:00.0
e0000000-efffffff : PCI MMCONFIG 0000 [bus 00-ff]
  e0000000-efffffff : pnp 00:06
f0000000-febfffff : PCI Bus 0000:00
  fcf76000-fcf77fff : 0000:00:09.0
    fcf76000-fcf77fff : ahci
  fcf78000-fcf7bfff : 0000:00:07.0
    fcf78000-fcf7bfff : ICH HD audio
  fcf7c000-fcf7cfff : 0000:00:0a.0
    fcf7c000-fcf7cfff : forcedeth
  fcf7d000-fcf7dfff : 0000:00:04.0
    fcf7d000-fcf7dfff : ohci_hcd
  fcf7e000-fcf7efff : 0000:00:02.0
    fcf7e000-fcf7efff : ohci_hcd
  fcf7f000-fcf7f00f : 0000:00:0a.0
    fcf7f000-fcf7f00f : forcedeth
  fcf7f400-fcf7f4ff : 0000:00:0a.0
    fcf7f400-fcf7f4ff : forcedeth
  fcf7f800-fcf7f8ff : 0000:00:04.1
    fcf7f800-fcf7f8ff : ehci_hcd
  fcf7fc00-fcf7fcff : 0000:00:02.1
    fcf7fc00-fcf7fcff : ehci_hcd
  fcf80000-fcffffff : 0000:00:01.3
  fd000000-febfffff : PCI Bus 0000:02
    fd000000-fdffffff : 0000:02:00.0
      fd000000-fdffffff : nvidia
    feb00000-feb7ffff : 0000:02:00.0
    febfc000-febfffff : 0000:02:00.1
      febfc000-febfffff : ICH HD audio
fec00000-fec00fff : reserved
  fec00000-fec003ff : IOAPIC 0
fed00000-fed00fff : PNP0103:00
  fed00000-fed003ff : HPET 0
fed04000-fed04fff : pnp 00:01
fee00000-feefffff : reserved
  fee00000-fee00fff : Local APIC
    fee00000-fee00fff : pnp 00:03
  fee01000-feefffff : pnp 00:01
fff00000-ffffffff : reserved
100000000-137ffffff : System RAM
```

This is on x86 with GRUB_BADRAM="0xb3a9feac,0xfffffffc". The address is a bit different now because I've exchanged slots those 2 memory sticks were in. I also noticed something interesting in dmesg, there is additional message in x64 kernel compared to x86, with same GRUB_BADRAM setting and nothing else:

```
init_memory_mapping: [mem 0x00100000-0xb3a9efff]
```

---

### Post by tgalati4 on 2015-05-20
It's interesting that the iomem shows this:  b3a9fc00-b3a9ffff : RAM buffer instead of BadRAM.  So either the 64 bit is really using that region as a RAM buffer (and that could cause a crash during boot) or the patch simply makes a dummy buffer that never gets used.

RAM is cheap, so perhaps there was no incentive to develop the badram module for 64-bit.  You could probably spend some time to examine the patch and see how it would fail in 64-bit mode.  My guess is the difference between the physical data path width and the virtual data-path width and how it changes with different CPU's.  With 32-bit, there was a more consistent data path width (as well as the 2 GB addressability limit).  With Physical Address Extension (PAE) and wider data buses, it would be difficult to write an algorithm to cover all Use Cases for bad RAM lockout.

---

### Post by UCyborg on 2015-05-20
From what I've seen in /proc/iomem and kernel logs, it really doesn't say much. iomem references same address range on both architectures, similarly with kernel logs, except that x64 makes some extra references for affected memory region or the regions around it. AFAIK, there are several ways to block bad RAM. GRUB_BADRAM is the universal method that works across Unix-like kernels and doesn't require extra code in kernel for handling bad memory. Another way is to use memmap parameter, again, this is available in kernel without any patches. I did try memmap, no luck on x64 kernel. Then we have Rick van Rein's BadRAM patch, which is only available for ancient kernel versions. I don't know if it would still work on recent kernels without modification.

What I find extremely strange, is after downloading kernel sources with apt-source and doing grep -r badram, there is no single reference to "badram" parameter in kernel code. It's only available as part of Rick van Rein's patch. And yet it still does something on my machine. No idea what to make out of this, especially after double-checking that I'm not confusing badram parameter with Grub's method.

Sure, it's a function that 99% of population won't miss, but if it happens, it's a nice thing to have. I have DDR2 type of RAM. Non-used modules are a bit pricy around here, it's better with used ones, but still, that would be throwing away 99,99% of functional memory and it's only a plus for Linux if it can handle it.
I might try out one of FreeBSD variants sometime to see how it handles it, would be interesting to know.

But nevertheless, there must be some kernel hacker out there who thoroughly understands how memory management works and why would same address translate differently on hardware level (if that's the case).

---

### Post by dino99 on 2015-05-20
with one of my system i also had such 'badram' errors but also kernel panic or random errors boot fail. That took me a long time to find the real reason of that mess : the bios was using the default (auto) ram settings, and testing the manual way, i decided to set the real voltage for that ddr2 ram (1.8v); and all the previous errors magically disappeared.

---

### Post by tgalati4 on 2015-05-20
To the OP, that is an excellent point.  Try declocking the RAM (lower the CAS timings) and lift the RAM voltages in BIOS, if possible.  It might be a simple fix.

---

### Post by UCyborg on 2015-05-20
Great news everyone!
I've found a working solution. Digging  through kernel documentation, I found out about built-in memtest.  Directly from Documentation/kernel-parameters.txt:
```
memtest=    [KNL,X86] Enable memtest
            Format: <integer>
            default : 0 <disable>
            Specifies the number of memtest passes to be
            performed. Each pass selects another test
            pattern from a given set of patterns. Memtest
            fills the memory with this pattern, validates
            memory contents and reserves bad memory
            regions that are detected.
```
After appending memtest=4 to my kernel command-line, I got this in dmesg:
```

[    0.000000] early_memtest: # of tests: 4
[    0.000000]   0000010000 - 0000097000 pattern aaaaaaaaaaaaaaaa
[    0.000000]   0000100000 - 0001000000 pattern aaaaaaaaaaaaaaaa
[    0.000000]   0001feb000 - 0035832000 pattern aaaaaaaaaaaaaaaa
[    0.000000]   0036c11000 - 00c7fa0000 pattern aaaaaaaaaaaaaaaa
[    0.000000]   0100000000 - 0137ffe000 pattern aaaaaaaaaaaaaaaa
[    0.000000]   aaaaaaaaaaaaaaaa bad mem addr 0133a9fea8 - 0133a9feb0 reserved
[    0.000000]   0133a9feb0 - 0137ffe000 pattern aaaaaaaaaaaaaaaa
[    0.000000]   0000010000 - 0000097000 pattern 5555555555555555
[    0.000000]   0000100000 - 0001000000 pattern 5555555555555555
[    0.000000]   0001feb000 - 0035832000 pattern 5555555555555555
[    0.000000]   0036c11000 - 00c7fa0000 pattern 5555555555555555
[    0.000000]   0100000000 - 0133a9fea8 pattern 5555555555555555
[    0.000000]   0133a9feb0 - 0137ffe000 pattern 5555555555555555
[    0.000000]   0000010000 - 0000097000 pattern ffffffffffffffff
[    0.000000]   0000100000 - 0001000000 pattern ffffffffffffffff
[    0.000000]   0001feb000 - 0035832000 pattern ffffffffffffffff
[    0.000000]   0036c11000 - 00c7fa0000 pattern ffffffffffffffff
[    0.000000]   0100000000 - 0133a9fea8 pattern ffffffffffffffff
[    0.000000]   0133a9feb0 - 0137ffe000 pattern ffffffffffffffff
[    0.000000]   0000010000 - 0000097000 pattern 0000000000000000
[    0.000000]   0000100000 - 0001000000 pattern 0000000000000000
[    0.000000]   0001feb000 - 0035832000 pattern 0000000000000000
[    0.000000]   0036c11000 - 00c7fa0000 pattern 0000000000000000
[    0.000000]   0100000000 - 0133a9fea8 pattern 0000000000000000
[    0.000000]   0133a9feb0 - 0137ffe000 pattern 0000000000000000
```
Memtest86 reports 133a9feac as bad address while Linux itself gives 133a9fea8. So it looks like address must be adjusted for x64 kernel, at least in my case. I'm not sure if I understand this correctly, but judging from that message, GRUB_BADRAM should be set to "0xb3a9fea8,0xfffffff8". Or just keep using memtest parameter, the surest way at least in my case where that region constantly fails and not at random. The only downside is that it adds about 3 seconds to boot time, no big deal though. My PC has been running fine now for over 2 hours :D
I did try adjusting timing and voltage settings in BIOS, it didn't help. Seems logical since both memory sticks have been fine for 5 years with auto settings. Funny though how in some cases auto settings fail, they're usually the safest to go with.

---

### Post by tgalati4 on 2015-05-20
I had a hunch that the addressing was slightly different.  I just didn't know how to find it.  Apparently you did.  This would be a good setting for servers that don't get booted frequently, but you want to more thoroughly check RAM during boot.   Everything is fixable in linux.  Patience is key.

---

### Post by UCyborg on 2015-05-22
Forget my last post, the part about different address, it's irrelevant, it's only different because Linux tests 8 bytes at once compared to Memtest86 that does 4. I think much of confusion regarding all of this comes from the fact that some memory is actually mapped above 4 GB and the fact how Memtest86 reports badram patterns. Long story short, I found correct value for GRUB_BADRAM, it's "0x0000000133a9feac,0xfffffffffffffffc". It seems badram patterns that it reports are only valid in 32-bit world. With 64-bit, the actual address that it reports as faulty must be taken into account, not the address it reports in BadRAM pattern reporting mode. Not quite sure about the mask, the easiest and clumsiest way would be switching to BadRAM pattern reporting mode...or it can be calculated from error bits or maybe some other data. Maybe Memtest86 6.x (EFI computers only) reports badram patterns correctly for x64, older versions don't, neither Memtest86 nor Memtest86+.

Or as an alternative, take a faulty address and shift bits to the right by 12, then use kernel parameter memmap like this:

memmap=4K$<result>,4K$<...>

Depends on where the parameter was entered, 1 or 3 backslashes might need to be added before dollar sign for it to work.

---

