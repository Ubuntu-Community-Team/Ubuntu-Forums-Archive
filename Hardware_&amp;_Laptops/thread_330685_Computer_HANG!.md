---
title: "Computer HANG!"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by hostage on 2007-01-03
Hello, it would be nice if someone could help me with this frustrating problem.
The computer HANG very often, i can't even move the mouse, the only thing i can do is to restart the computer :neutral:  i assume it depends on the Ram memory? Im very very new in Linux i have used it for like 2 months, i will never install windows again! Sorry my english is not very good.

some info about my hardware

Os: Ubuntu Edgy
Motherboard: AsRock 939Dual-SATA2
Cpu: Amd Athlon 64 2400mhz
Ram: 2x512 dualram
Graphic: Geforce 7600gs 256mb

This is the log from "system log, messages"
_________________________________________________________________________________________________________
Jan  3 11:56:04 anders syslogd 1.4.1#18ubuntu6: restart.
Jan  3 11:56:04 anders kernel: Inspecting /boot/System.map-2.6.17-10-386
Jan  3 11:56:04 anders kernel: Loaded 22426 symbols from /boot/System.map-2.6.17-10-386.
Jan  3 11:56:04 anders kernel: Symbols match kernel version 2.6.17.
Jan  3 11:56:04 anders kernel: No module symbols loaded - kernel modules not enabled. 
Jan  3 11:56:04 anders kernel: [17179569.184000] Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006 (Ubuntu 2.6.17-10.34-386)
_________________________________________________________________________________________________________

[B]Jan  3 11:56:04 anders kernel: [17179569.184000] BIOS-provided physical RAM map:
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
Jan  3 11:56:04 anders kernel: [17179569.184000] 127MB HIGHMEM available.
Jan  3 11:56:04 anders kernel: [17179569.184000] 896MB LOWMEM available.[/B]
Jan  3 11:56:04 anders kernel: [17179569.184000] found SMP MP-table at 000ff780
Jan  3 11:56:04 anders kernel: [17179569.184000] DMI present.
Jan  3 11:56:04 anders kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x808
Jan  3 11:56:04 anders kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan  3 11:56:04 anders kernel: [17179569.184000] Processor #0 15:15 APIC version 16

________________________________________________________________________________________________________

the only thing i understand is that the bios sending the "Message log" something about a ram memory problem, but i dont understand anything from the message! Would be very nice if someone could help me to solve the very frustrating problem. :D

---

### Post by budgie9 on 2007-01-03
> **hostage said:**
> Hello, it would be nice if someone could help me with this frustrating problem.
The computer HANG very often, i can't even move the mouse, the only thing i can do is to restart the computer :neutral:  i assume it depends on the Ram memory? Im very very new in Linux i have used it for like 2 months, i will never install windows again! Sorry my english is not very good.

some info about my hardware

Os: Ubuntu Edgy
Motherboard: AsRock 939Dual-SATA2
Cpu: Amd Athlon 64 2400mhz
Ram: 2x512 dualram
Graphic: Geforce 7600gs 256mb

This is the log from "system log, messages"
_________________________________________________________________________________________________________
Jan  3 11:56:04 anders syslogd 1.4.1#18ubuntu6: restart.
Jan  3 11:56:04 anders kernel: Inspecting /boot/System.map-2.6.17-10-386
Jan  3 11:56:04 anders kernel: Loaded 22426 symbols from /boot/System.map-2.6.17-10-386.
Jan  3 11:56:04 anders kernel: Symbols match kernel version 2.6.17.
Jan  3 11:56:04 anders kernel: No module symbols loaded - kernel modules not enabled. 
Jan  3 11:56:04 anders kernel: [17179569.184000] Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006 (Ubuntu 2.6.17-10.34-386)
_________________________________________________________________________________________________________

[B]Jan  3 11:56:04 anders kernel: [17179569.184000] BIOS-provided physical RAM map:
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
Jan  3 11:56:04 anders kernel: [17179569.184000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
Jan  3 11:56:04 anders kernel: [17179569.184000] 127MB HIGHMEM available.
Jan  3 11:56:04 anders kernel: [17179569.184000] 896MB LOWMEM available.[/B]
Jan  3 11:56:04 anders kernel: [17179569.184000] found SMP MP-table at 000ff780
Jan  3 11:56:04 anders kernel: [17179569.184000] DMI present.
Jan  3 11:56:04 anders kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x808
Jan  3 11:56:04 anders kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan  3 11:56:04 anders kernel: [17179569.184000] Processor #0 15:15 APIC version 16

________________________________________________________________________________________________________

the only thing i understand is that the bios sending the "Message log" something about a ram memory problem, but i dont understand anything from the message! Would be very nice if someone could help me to solve the very frustrating problem. :D

If you suspect it is memory, then run the Memtest86 program on the CD. You can also download it.
This will indicate if there is a memory problem, a fault stick perhaps.

[http://www.memtest86.com/](http://www.memtest86.com/)

---

### Post by hostage on 2007-01-04
Im so new i don't even know how to install "memtest" i get this error when i try to "make"

____________________________________________________________________________________________________
anders@anders:~/Desktop/memtest86-3.2$ make
gcc -E -m32 -traditional head.S -o head.s
as -32 -o head.o head.s
gcc -c -m32 -fPIC -Wall -O -fno-strict-aliasing reloc.c
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC main.c
main.c: In function &#8216;find_ticks&#8217;:
main.c:442: warning: comparisons like X<=Y<=Z do not have their mathematical meaning
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding test.c
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC init.c
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC lib.c
lib.c: In function &#8216;inter&#8217;:
lib.c:384: warning: pointer targets in assignment differ in signedness
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC patn.c
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC screen_buffer.c
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC config.c
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC linuxbios.c
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC memsize.c
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC pci.c
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC controller.c
gcc    -c -o random.o random.c
gcc -c -Wall -march=i486 -m32 -Os -fomit-frame-pointer -fno-builtin -ffreestanding -fPIC extra.c
ld --warn-constructors --warn-common -static -T memtest_shared.lds -o memtest_shared head.o reloc.o main.o test.o init.o lib.o patn.o screen_buffer.o config.o linuxbios.o memsize.o pci.o controller.o random.o extra.o && \
        ld -shared -Bsymbolic -T memtest_shared.lds -o memtest_shared head.o reloc.o main.o test.o init.o lib.o patn.o screen_buffer.o config.o linuxbios.o memsize.o pci.o controller.o random.o extra.o
lib.o: In function `.L152':
lib.c:(.text+0x915): undefined reference to `__stack_chk_fail_local'
make: *** [memtest_shared] Error 1
_______________________________________________________________________________________________________________________________________________________________________

---

### Post by Wim Sturkenboom on 2007-01-04
As said, memtest is available on the install CDs (for sure on the live one, also on alternate CD if I recall correctly). Boot from CD and select the memtest option.

By the way, where do you see a memory problem?

Which driver do you use for your video card? I had short freezes (not hangs) when I used the nv driver.

---

### Post by hostage on 2007-01-04
This maybe is the RAM problem?

"Jan 3 11:56:04 anders kernel: [17179569.184000] BIOS-provided physical RAM map:"

I use "nvidia driver version: 1.0-9746" i used ENVY to update to the newest.

Ok i will boot from the live cd and test it and see what kind of a problem it may be! ;)

My computer hang and sometimes it sounds strange, like a constantly beep, the computer force me to
restart it to make it work again

Now i have tested memtest and i don't get any errors! Now i have no idea what kind of problem it can be!

---

### Post by hostage on 2007-01-04
I found a strange thing, if you look at the time of the messages, all of these messages appears at the same time "08:39:44" and after the long message i force to restart the computer. And when i tested MEMTEST i found out that it wasn't any problem with the memory. Now have no idea what it can be! Someone please help me :confused: 

ooh i forgott to tell, i use the 32 bit version of ubuntu even though i have a amd64 cpu, can that cause the problem? The reason why i use the 32bit version of ubuntu is that WINE won't work under 64bit ubuntu version.
________________________________________________________________________________________________________
Jan  3 **08:39:44** anders syslogd 1.4.1#18ubuntu6: **restart.**
Jan  **3 08:39:44** anders kernel: Inspecting /boot/System.map-2.6.17-10-386
Jan  3 08:39:44 anders kernel: Loaded 22426 symbols from /boot/System.map-2.6.17-10-386.
Jan  3 08:39:44 anders kernel: Symbols match kernel version 2.6.17.
Jan  3 08:39:44 anders kernel: No module symbols loaded - kernel modules not enabled. 
Jan  3 08:39:44 anders kernel: [17179569.184000] Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006 (Ubuntu 2.6.17-10.34-386)
Jan  3 08:39:44 anders kernel: [17179569.184000] BIOS-provided physical RAM map:
Jan  3 08:39:44 anders kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jan  3 08:39:44 anders kernel: [17179569.184000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Jan  3 08:39:44 anders kernel: [17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Jan  3 08:39:44 anders kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
Jan  3 08:39:44 anders kernel: [17179569.184000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
Jan  3 08:39:44 anders kernel: [17179569.184000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
Jan  3 08:39:44 anders kernel: [17179569.184000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
Jan  3 08:39:44 anders kernel: [17179569.184000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
Jan  3 08:39:44 anders kernel: [17179569.184000] 127MB HIGHMEM available.
Jan  3 08:39:44 anders kernel: [17179569.184000] 896MB LOWMEM available.
Jan  3 08:39:44 anders kernel: [17179569.184000] found SMP MP-table at 000ff780
Jan  3 08:39:44 anders kernel: [17179569.184000] DMI present.
Jan  3 08:39:44 anders kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x808
Jan  3 08:39:44 anders kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jan  3 08:39:44 anders kernel: [17179569.184000] Processor #0 15:15 APIC version 16
Jan  3 08:39:44 anders kernel: [17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
Jan  3 08:39:44 anders kernel: [17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jan  3 08:39:44 anders kernel: [17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Jan  3 08:39:44 anders kernel: [17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec10000] gsi_base[24])
Jan  3 08:39:44 anders kernel: [17179569.184000] IOAPIC[1]: apic_id 2, version 17, address 0xfec10000, GSI 24-39
Jan  3 08:39:44 anders kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan  3 08:39:44 anders kernel: [17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jan  3 08:39:44 anders kernel: [17179569.184000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Jan  3 08:39:44 anders kernel: [17179569.184000] Using ACPI (MADT) for SMP configuration information
Jan  3 08:39:44 anders kernel: [17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf380000)
Jan  3 08:39:44 anders kernel: [17179569.184000] Built 1 zonelists
Jan  3 08:39:44 anders kernel: [17179569.184000] Kernel command line: root=/dev/sda3 ro quiet splash
Jan  3 08:39:44 anders kernel: [17179569.184000] Enabling fast FPU save and restore... done.
Jan  3 08:39:44 anders kernel: [17179569.184000] Enabling unmasked SIMD FPU exception support... done.
Jan  3 08:39:44 anders kernel: [17179569.184000] Initializing CPU#0
Jan  3 08:39:44 anders kernel: [17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jan  3 08:39:44 anders kernel: [17179569.184000] Detected 2400.395 MHz processor.
Jan  3 08:39:44 anders kernel: [17179569.184000] Using pmtmr for high-res timesource
Jan  3 08:39:44 anders kernel: [17179569.184000] Console: colour VGA+ 80x25
Jan  3 08:39:44 anders kernel: [17179569.848000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  3 08:39:44 anders kernel: [17179569.848000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  3 08:39:44 anders kernel: [17179569.860000] Memory: 1029680k/1048256k available (1829k kernel code, 17812k reserved, 1038k data, 288k init, 130752k highmem)
Jan  3 08:39:44 anders kernel: [17179569.860000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jan  3 08:39:44 anders kernel: [17179569.940000] Calibrating delay using timer specific routine.. 4804.28 BogoMIPS (lpj=9608560)
Jan  3 08:39:44 anders kernel: [17179569.940000] Security Framework v1.0.0 initialized
Jan  3 08:39:44 anders kernel: [17179569.940000] SELinux:  Disabled at boot.
Jan  3 08:39:44 anders kernel: [17179569.940000] Mount-cache hash table entries: 512
Jan  3 08:39:44 anders kernel: [17179569.940000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jan  3 08:39:44 anders kernel: [17179569.940000] CPU: L2 Cache: 512K (64 bytes/line)
Jan  3 08:39:44 anders kernel: [17179569.940000] CPU: AMD Athlon(tm) 64 Processor 3800+ stepping 02
Jan  3 08:39:44 anders kernel: [17179569.940000] Checking 'hlt' instruction... OK.
Jan  3 08:39:44 anders kernel: [17179569.956000] SMP alternatives: switching to UP code
Jan  3 08:39:44 anders kernel: [17179569.956000] Freeing SMP alternatives: 0k freed
Jan  3 08:39:44 anders kernel: [17179569.956000] checking if image is initramfs... it is
Jan  3 08:39:44 anders kernel: [17179570.316000] Freeing initrd memory: 5251k freed
Jan  3 08:39:44 anders kernel: [17179570.316000] ACPI: Core revision 20060707
Jan  3 08:39:44 anders kernel: [17179570.316000] ACPI: Looking for DSDT ... not found!
Jan  3 08:39:44 anders kernel: [17179570.320000] ENABLING IO-APIC IRQs
Jan  3 08:39:44 anders kernel: [17179570.320000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan  3 08:39:44 anders kernel: [17179570.464000] NET: Registered protocol family 16
Jan  3 08:39:44 anders kernel: [17179570.464000] EISA bus registered
Jan  3 08:39:44 anders kernel: [17179570.464000] ACPI: bus type pci registered
Jan  3 08:39:44 anders kernel: [17179570.464000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
Jan  3 08:39:44 anders kernel: [17179570.464000] PCI: Not using MMCONFIG.
Jan  3 08:39:44 anders kernel: [17179570.464000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
Jan  3 08:39:44 anders kernel: [17179570.464000] PCI: Using configuration type 1
Jan  3 08:39:44 anders kernel: [17179570.464000] Setting up standard PCI resources
Jan  3 08:39:44 anders kernel: [17179570.472000] ACPI: Interpreter enabled
Jan  3 08:39:44 anders kernel: [17179570.472000] ACPI: Using IOAPIC for interrupt routing
Jan  3 08:39:44 anders kernel: [17179570.472000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan  3 08:39:44 anders kernel: [17179570.476000] PCI quirk: region 0800-083f claimed by ali7101 ACPI
Jan  3 08:39:44 anders kernel: [17179570.476000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:12.0
Jan  3 08:39:44 anders kernel: [17179570.476000] PCI: Transparent bridge - 0000:00:06.0
Jan  3 08:39:44 anders kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15), disabled.
Jan  3 08:39:44 anders kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jan  3 08:39:44 anders kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15), disabled.
Jan  3 08:39:44 anders kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jan  3 08:39:44 anders kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jan  3 08:39:44 anders kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jan  3 08:39:44 anders kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Jan  3 08:39:44 anders kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
Jan  3 08:39:44 anders kernel: [17179570.492000] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Jan  3 08:39:44 anders kernel: [17179570.492000] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan  3 08:39:44 anders kernel: [17179570.492000] pnp: PnP ACPI init
Jan  3 08:39:44 anders kernel: [17179570.496000] pnp: PnP ACPI: found 17 devices
Jan  3 08:39:44 anders kernel: [17179570.496000] PnPBIOS: Disabled by ACPI PNP
Jan  3 08:39:44 anders kernel: [17179570.496000] PCI: Using ACPI for IRQ routing
Jan  3 08:39:44 anders kernel: [17179570.496000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jan  3 08:39:44 anders kernel: [17179570.504000] pnp: 00:0e: ioport range 0x290-0x29f has been reserved
Jan  3 08:39:44 anders kernel: [17179570.504000] PCI: Bridge: 0000:00:01.0
Jan  3 08:39:44 anders kernel: [17179570.504000]   IO window: d000-dfff
Jan  3 08:39:44 anders kernel: [17179570.504000]   MEM window: f5000000-f7efffff
Jan  3 08:39:44 anders kernel: [17179570.504000]   PREFETCH window: d0000000-dfffffff
Jan  3 08:39:44 anders kernel: [17179570.504000] PCI: Bridge: 0000:00:02.0
Jan  3 08:39:44 anders kernel: [17179570.504000]   IO window: disabled.
Jan  3 08:39:44 anders kernel: [17179570.504000]   MEM window: disabled.
Jan  3 08:39:44 anders kernel: [17179570.504000]   PREFETCH window: f3f00000-f3ffffff
Jan  3 08:39:44 anders kernel: [17179570.504000] PCI: Bridge: 0000:00:05.0
Jan  3 08:39:44 anders kernel: [17179570.504000]   IO window: disabled.
Jan  3 08:39:44 anders kernel: [17179570.504000]   MEM window: disabled.
Jan  3 08:39:44 anders kernel: [17179570.504000]   PREFETCH window: disabled.
Jan  3 08:39:44 anders kernel: [17179570.504000] PCI: Bridge: 0000:00:06.0
Jan  3 08:39:44 anders kernel: [17179570.504000]   IO window: e000-efff
Jan  3 08:39:44 anders kernel: [17179570.504000]   MEM window: f7f00000-f7ffffff
Jan  3 08:39:44 anders kernel: [17179570.504000]   PREFETCH window: disabled.
Jan  3 08:39:44 anders kernel: [17179570.504000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 29 (level, low) -> IRQ 169
Jan  3 08:39:44 anders kernel: [17179570.504000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 34 (level, low) -> IRQ 177
Jan  3 08:39:44 anders kernel: [17179570.504000] NET: Registered protocol family 2
Jan  3 08:39:44 anders kernel: [17179570.544000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan  3 08:39:44 anders kernel: [17179570.544000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
Jan  3 08:39:44 anders kernel: [17179570.544000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
Jan  3 08:39:44 anders kernel: [17179570.544000] TCP: Hash tables configured (established 131072 bind 65536)
Jan  3 08:39:44 anders kernel: [17179570.544000] TCP reno registered
Jan  3 08:39:44 anders kernel: [17179570.544000] audit: initializing netlink socket (disabled)
Jan  3 08:39:44 anders kernel: [17179570.544000] audit(1167809964.544:1): initialized
Jan  3 08:39:44 anders kernel: [17179570.544000] highmem bounce pool size: 64 pages
Jan  3 08:39:44 anders kernel: [17179570.544000] VFS: Disk quotas dquot_6.5.1
Jan  3 08:39:44 anders kernel: [17179570.544000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan  3 08:39:44 anders kernel: [17179570.544000] Initializing Cryptographic API
Jan  3 08:39:44 anders kernel: [17179570.544000] io scheduler noop registered
Jan  3 08:39:44 anders kernel: [17179570.544000] io scheduler anticipatory registered
Jan  3 08:39:44 anders kernel: [17179570.544000] io scheduler deadline registered
Jan  3 08:39:44 anders kernel: [17179570.544000] io scheduler cfq registered (default)
Jan  3 08:39:44 anders kernel: [17179570.976000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 29 (level, low) -> IRQ 169
Jan  3 08:39:44 anders kernel: [17179570.976000] assign_interrupt_mode Found MSI capability
Jan  3 08:39:44 anders kernel: [17179570.976000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 34 (level, low) -> IRQ 177
Jan  3 08:39:44 anders kernel: [17179570.976000] assign_interrupt_mode Found MSI capability
Jan  3 08:39:44 anders kernel: [17179570.976000] isapnp: Scanning for PnP cards...
Jan  3 08:39:44 anders kernel: [17179571.328000] isapnp: No Plug & Play device found
Jan  3 08:39:44 anders kernel: [17179571.340000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jan  3 08:39:44 anders kernel: [17179571.340000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan  3 08:39:44 anders kernel: [17179571.340000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Jan  3 08:39:44 anders kernel: [17179571.340000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan  3 08:39:44 anders kernel: [17179571.340000] mice: PS/2 mouse device common for all mice
Jan  3 08:39:44 anders kernel: [17179571.344000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jan  3 08:39:44 anders kernel: [17179571.344000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jan  3 08:39:44 anders kernel: [17179571.344000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jan  3 08:39:44 anders kernel: [17179571.344000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jan  3 08:39:44 anders kernel: [17179571.344000] PNP: PS/2 controller doesn't have AUX irq; using default 12
Jan  3 08:39:44 anders kernel: [17179571.344000] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan  3 08:39:44 anders kernel: [17179571.344000] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan  3 08:39:44 anders kernel: [17179571.344000] EISA: Probing bus 0 at eisa.0
Jan  3 08:39:44 anders kernel: [17179571.344000] EISA: Detected 0 cards.
Jan  3 08:39:44 anders kernel: [17179571.344000] TCP bic registered
Jan  3 08:39:44 anders kernel: [17179571.344000] NET: Registered protocol family 1
Jan  3 08:39:44 anders kernel: [17179571.344000] NET: Registered protocol family 8
Jan  3 08:39:44 anders kernel: [17179571.344000] NET: Registered protocol family 20
Jan  3 08:39:44 anders kernel: [17179571.344000] Using IPI Shortcut mode
Jan  3 08:39:44 anders kernel: [17179571.344000] ACPI: (supports S0 S1 S3 S4 S5)
Jan  3 08:39:44 anders kernel: [17179571.344000] Freeing unused kernel memory: 288k freed
Jan  3 08:39:44 anders kernel: [17179572.404000] Capability LSM initialized
Jan  3 08:39:44 anders kernel: [17179572.696000] ALI15X3: IDE controller at PCI slot 0000:00:12.0
Jan  3 08:39:44 anders kernel: [17179572.696000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 19 (level, low) -> IRQ 209
Jan  3 08:39:44 anders kernel: [17179572.696000] ALI15X3: chipset revision 199
Jan  3 08:39:44 anders kernel: [17179572.696000] ALI15X3: not 100%% native mode: will probe irqs later
Jan  3 08:39:44 anders kernel: [17179572.696000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:DMA
Jan  3 08:39:44 anders kernel: [17179572.696000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:pio, hdd:pio
Jan  3 08:39:44 anders kernel: [17179573.712000] hdb: TSSTcorpCD/DVDW SH-W162C, ATAPI CD/DVD-ROM drive
Jan  3 08:39:44 anders kernel: [17179573.768000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Jan  3 08:39:44 anders kernel: [17179574.348000] hdb: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
Jan  3 08:39:44 anders kernel: [17179574.348000] Uniform CD-ROM driver Revision: 3.20
Jan  3 08:39:44 anders kernel: [17179574.380000] SCSI subsystem initialized
Jan  3 08:39:44 anders kernel: [17179574.380000] sata_uli 0000:00:12.1: version 0.5
Jan  3 08:39:44 anders kernel: [17179574.380000] ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 19 (level, low) -> IRQ 209
Jan  3 08:39:44 anders kernel: [17179574.380000] ata1: SATA max UDMA/133 cmd 0xCC00 ctl 0xC482 bmdma 0xC000 irq 209
Jan  3 08:39:44 anders kernel: [17179574.380000] ata2: SATA max UDMA/133 cmd 0xC400 ctl 0xC082 bmdma 0xC008 irq 209
Jan  3 08:39:44 anders kernel: [17179574.588000] ata1: SATA link up 1.5 Gbps (SStatus 113)
Jan  3 08:39:44 anders kernel: [17179574.596000] ata1: dev 0 ATA-7, max UDMA/133, 398297088 sectors: LBA48
Jan  3 08:39:44 anders kernel: [17179574.604000] ata1: dev 0 configured for UDMA/133
Jan  3 08:39:44 anders kernel: [17179574.604000] scsi0 : sata_uli
Jan  3 08:39:44 anders kernel: [17179574.808000] ata2: SATA link up 1.5 Gbps (SStatus 113)
Jan  3 08:39:44 anders kernel: [17179574.816000] ata2: dev 0 ATA-7, max UDMA/133, 490234752 sectors: LBA48
Jan  3 08:39:44 anders kernel: [17179574.824000] ata2: dev 0 configured for UDMA/133
Jan  3 08:39:44 anders kernel: [17179574.824000] scsi1 : sata_uli
Jan  3 08:39:44 anders kernel: [17179574.824000]   Vendor: ATA       Model: Maxtor 6B200M0    Rev: BANC
Jan  3 08:39:44 anders kernel: [17179574.824000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Jan  3 08:39:44 anders kernel: [17179574.824000]   Vendor: ATA       Model: Maxtor 6L250S0    Rev: BANC
Jan  3 08:39:44 anders kernel: [17179574.824000]   Type:   Direct-Access                      ANSI SCSI revision: 05
Jan  3 08:39:44 anders kernel: [17179574.832000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
Jan  3 08:39:44 anders kernel: [17179574.832000] sda: Write Protect is off
Jan  3 08:39:44 anders kernel: [17179574.832000] SCSI device sda: drive cache: write back
Jan  3 08:39:44 anders kernel: [17179574.832000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
Jan  3 08:39:44 anders kernel: [17179574.832000] sda: Write Protect is off
Jan  3 08:39:44 anders kernel: [17179574.832000] SCSI device sda: drive cache: write back
Jan  3 08:39:44 anders kernel: [17179574.832000]  sda: sda1 sda2 < sda5 > sda3
Jan  3 08:39:44 anders kernel: [17179574.880000] sd 0:0:0:0: Attached scsi disk sda
Jan  3 08:39:44 anders kernel: [17179574.884000] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
Jan  3 08:39:44 anders kernel: [17179574.884000] sdb: Write Protect is off
Jan  3 08:39:44 anders kernel: [17179574.884000] SCSI device sdb: drive cache: write back
Jan  3 08:39:44 anders kernel: [17179574.888000] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
Jan  3 08:39:44 anders kernel: [17179574.888000] sdb: Write Protect is off
Jan  3 08:39:44 anders kernel: [17179574.888000] SCSI device sdb: drive cache: write back
Jan  3 08:39:44 anders kernel: [17179574.888000]  sdb: sdb1 < sdb5 >
Jan  3 08:39:44 anders kernel: [17179574.916000] sd 1:0:0:0: Attached scsi disk sdb
Jan  3 08:39:44 anders kernel: [17179575.148000] usbcore: registered new driver usbfs
Jan  3 08:39:44 anders kernel: [17179575.148000] usbcore: registered new driver hub
Jan  3 08:39:44 anders kernel: [17179575.148000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 20 (level, low) -> IRQ 217
Jan  3 08:39:44 anders kernel: [17179575.148000] ohci_hcd 0000:00:13.0: OHCI Host Controller
Jan  3 08:39:44 anders kernel: [17179575.148000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Jan  3 08:39:44 anders kernel: [17179575.172000] ohci_hcd 0000:00:13.0: irq 217, io mem 0xf4ffe000
Jan  3 08:39:44 anders kernel: [17179575.228000] usb usb1: configuration #1 chosen from 1 choice
Jan  3 08:39:44 anders kernel: [17179575.228000] hub 1-0:1.0: USB hub found
Jan  3 08:39:44 anders kernel: [17179575.228000] hub 1-0:1.0: 3 ports detected
Jan  3 08:39:44 anders kernel: [17179575.332000] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 21 (level, low) -> IRQ 225
Jan  3 08:39:44 anders kernel: [17179575.332000] ohci_hcd 0000:00:13.1: OHCI Host Controller
Jan  3 08:39:44 anders kernel: [17179575.332000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Jan  3 08:39:44 anders kernel: [17179575.348000] ohci_hcd 0000:00:13.1: irq 225, io mem 0xf4ffd000
Jan  3 08:39:44 anders kernel: [17179575.404000] usb usb2: configuration #1 chosen from 1 choice
Jan  3 08:39:44 anders kernel: [17179575.404000] hub 2-0:1.0: USB hub found
Jan  3 08:39:44 anders kernel: [17179575.404000] hub 2-0:1.0: 3 ports detected
Jan  3 08:39:44 anders kernel: [17179575.520000] ACPI: PCI Interrupt 0000:00:13.3[D] -> GSI 23 (level, low) -> IRQ 233
Jan  3 08:39:44 anders kernel: [17179575.520000] ehci_hcd 0000:00:13.3: EHCI Host Controller
Jan  3 08:39:44 anders kernel: [17179575.520000] ehci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 3
Jan  3 08:39:44 anders kernel: [17179575.520000] ehci_hcd 0000:00:13.3: debug port 1
Jan  3 08:39:44 anders kernel: [17179575.544000] ehci_hcd 0000:00:13.3: irq 233, io mem 0xf4fff800
Jan  3 08:39:44 anders kernel: [17179575.544000] ehci_hcd 0000:00:13.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan  3 08:39:44 anders kernel: [17179575.544000] usb usb3: configuration #1 chosen from 1 choice
Jan  3 08:39:44 anders kernel: [17179575.544000] hub 3-0:1.0: USB hub found
Jan  3 08:39:44 anders kernel: [17179575.544000] hub 3-0:1.0: 8 ports detected
Jan  3 08:39:44 anders kernel: [17179575.692000] Attempting manual resume
Jan  3 08:39:44 anders kernel: [17179575.704000] kjournald starting.  Commit interval 5 seconds
Jan  3 08:39:44 anders kernel: [17179575.704000] EXT3-fs: mounted filesystem with ordered data mode.
Jan  3 08:39:44 anders kernel: [17179576.684000] usb 2-1: new low speed USB device using ohci_hcd and address 2
Jan  3 08:39:44 anders kernel: [17179576.916000] usb 2-1: configuration #1 chosen from 1 choice
Jan  3 08:39:44 anders kernel: [17179577.224000] usb 2-2: new low speed USB device using ohci_hcd and address 3
Jan  3 08:39:44 anders kernel: [17179577.436000] usb 2-2: configuration #1 chosen from 1 choice
Jan  3 08:39:44 anders kernel: [17179582.608000] input: PC Speaker as /class/input/input0
Jan  3 08:39:44 anders kernel: [17179582.776000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  3 08:39:44 anders kernel: [17179582.784000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan  3 08:39:44 anders kernel: [17179582.796000] Linux agpgart interface v0.101 (c) Dave Jones
Jan  3 08:39:44 anders kernel: [17179582.796000] agpgart: Detected AGP bridge 20
Jan  3 08:39:44 anders kernel: [17179582.796000] Setting up ULi AGP.
Jan  3 08:39:44 anders kernel: [17179582.800000] agpgart: AGP aperture is 64M @ 0xcc000000
Jan  3 08:39:44 anders kernel: [17179582.828000] parport: PnPBIOS parport detected.
Jan  3 08:39:44 anders kernel: [17179582.828000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jan  3 08:39:44 anders kernel: [17179583.064000] Real Time Clock Driver v1.12ac
Jan  3 08:39:44 anders kernel: [17179583.088000] ali1535_smbus 0000:00:07.1: ALI1535_smb region uninitialized - upgrade BIOS?
Jan  3 08:39:44 anders kernel: [17179583.088000] ali1535_smbus 0000:00:07.1: ALI1535 not detected, module not inserted.
Jan  3 08:39:44 anders kernel: [17179583.120000] ali1563: SMBus control = 0403
Jan  3 08:39:44 anders kernel: [17179583.120000] ali1563_probe: Returning 0
Jan  3 08:39:44 anders kernel: [17179583.288000] NET: Registered protocol family 23
Jan  3 08:39:44 anders kernel: [17179583.308000] Floppy drive(s): fd0 is 1.44M
Jan  3 08:39:44 anders kernel: [17179583.328000] FDC 0 is a post-1991 82077
Jan  3 08:39:44 anders kernel: [17179583.336000] Loading module: rt61pci - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
Jan  3 08:39:44 anders kernel: [17179583.336000] ACPI: PCI Interrupt 0000:04:05.0[A] -> GSI 20 (level, low) -> IRQ 217
Jan  3 08:39:44 anders kernel: [17179583.440000] uli526x: ULi M5261/M5263 net driver, version 0.9.3 (2005-7-29)
Jan  3 08:39:44 anders kernel: [17179583.508000] gameport: EMU10K1 is pci0000:04:06.1/gameport0, io 0xe880, speed 1028kHz
Jan  3 08:39:44 anders kernel: [17179583.512000] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 17 (level, low) -> IRQ 50
Jan  3 08:39:44 anders kernel: [17179583.536000] eth0: ULi M5263 at pci0000:00:11.0, 00:13:8f:c9:f2:e2, irq 50.
Jan  3 08:39:44 anders kernel: [17179583.880000] nvidia: module license 'NVIDIA' taints kernel.
Jan  3 08:39:44 anders kernel: [17179583.884000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 25 (level, low) -> IRQ 58
Jan  3 08:39:44 anders kernel: [17179583.884000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan  3 08:39:44 anders kernel: [17179584.348000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan  3 08:39:44 anders kernel: [17179584.348000] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jan  3 08:39:44 anders kernel: [17179584.444000] ACPI: PCI Interrupt 0000:04:06.0[A] -> GSI 21 (level, low) -> IRQ 225
Jan  3 08:39:44 anders kernel: [17179584.712000] usbcore: registered new driver hiddev
Jan  3 08:39:44 anders kernel: [17179584.728000] input: Logitech HID compliant keyboard as /class/input/input1
Jan  3 08:39:44 anders kernel: [17179584.728000] input: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:00:13.1-1
Jan  3 08:39:44 anders kernel: [17179584.776000] input: Logitech HID compliant keyboard as /class/input/input2
Jan  3 08:39:44 anders kernel: [17179584.776000] input: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:00:13.1-1
Jan  3 08:39:44 anders kernel: [17179584.784000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
Jan  3 08:39:44 anders kernel: [17179584.784000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.1-2
Jan  3 08:39:44 anders kernel: [17179584.784000] usbcore: registered new driver usbhid
Jan  3 08:39:44 anders kernel: [17179584.784000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jan  3 08:39:44 anders kernel: [17179584.976000] ts: Compaq touchscreen protocol output
Jan  3 08:39:44 anders kernel: [17179585.144000] lp0: using parport0 (interrupt-driven).
Jan  3 08:39:44 anders kernel: [17179585.164000] fuse init (API version 7.6)
Jan  3 08:39:44 anders kernel: [17179585.188000] Adding 1847464k swap on /dev/disk/by-uuid/110d8cd4-f678-40a1-9abf-17c9bee4ea33.  Priority:-1 extents:1 across:1847464k
Jan  3 08:39:44 anders kernel: [17179585.252000] EXT3 FS on sda3, internal journal
Jan  3 08:39:44 anders kernel: [17179585.740000] NET: Registered protocol family 17
Jan  3 08:39:44 anders kernel: [17179587.708000] uli526x: eth0 NIC Link is Up 100 Mbps Full duplex
Jan  3 08:39:44 anders kernel: [17179588.532000] NET: Registered protocol family 10
Jan  3 08:39:44 anders kernel: [17179588.532000] lo: Disabled Privacy Extensions
Jan  3 08:39:44 anders kernel: [17179588.532000] IPv6 over IPv4 tunneling driver
Jan  3 08:39:44 anders kernel: [17179589.872000] ACPI: Power Button (FF) [PWRF]
Jan  3 08:39:44 anders kernel: [17179589.872000] ACPI: Power Button (CM) [PWRB]
Jan  3 08:39:44 anders kernel: [17179589.976000] pcc_acpi: loading...
Jan  3 08:39:44 anders kernel: [17179590.208000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
Jan  3 08:39:44 anders kernel: [17179590.240000] acpi_cpufreq: Unknown symbol cpu_online_map
________________________________________________________________________________________________________

---

### Post by Wim Sturkenboom on 2007-01-04
32bit version is OK (use it as well on AMD 64 bit). And the 08:39:44 is probably the time that your system started.
Can't help you further (unfortunately).

---

### Post by atonello on 2007-01-05
Maybe we have a similar problem, please read here
[http://www.ubuntuforums.org/showthread.php?t=330070](http://www.ubuntuforums.org/showthread.php?t=330070)

---

### Post by RandomJoe on 2007-01-05
I had similar freezes on my brand new C2D system when trying to run multiple monitors and the nVidia drivers, and after some searching on the nVforum found a suggestion to try adding "pci=nommconf" to the kernel boot string.  Works like a dream now!  Perhaps that'll help...?

---

### Post by neil.the.blue on 2007-01-10
I too had this problem and found the kernel option fixed it. However do be careful to use the right case:

pci=NOMMCONF worked
pci=nommconf had no effect

Hope this helps

Neil

---

### Post by RandomJoe on 2007-01-10
That's strange - I used the lowercase version and it's working fine on my system.  (At least, if I remove it the system will hang!)

---

