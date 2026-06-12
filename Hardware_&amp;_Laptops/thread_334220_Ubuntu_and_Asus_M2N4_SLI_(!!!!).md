---
title: "Ubuntu and Asus M2N4 SLI? (!!!!)"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by atlien on 2007-01-08
I've been trying to make Ubuntu work (goodbye Windows) but I keep getting this error telling me to disable apic (what is that?), to 'noapic' upon boot.  So I do that and the Ubuntu 6.10 runs fine from live cd with the exception of wireless, but that's for later.

Once I install and remove cd to boot from HD, I can't get in.  I get an error during startup.  Something about 'grub'.  Then it just stops.  Not a freeze.  Almost like a halt on error type stoppage, meaning dos screen/flashing cursor but can't type or do anything.  The only thing I can ever do at this point is reboot to start the cycle over again.

Has anyone had any luck with the M2N4 motherboard from Asus?  And what is noapic?  Is there something I can do to 'noapic' permanently (instead of temporary with the live cd) so that I can run Ubuntu 6.10 on my Asus M2N4?

Any help would be appreciated.  Thanks!

---

### Post by hal10000 on 2007-01-08
APIC stands for Advanced Programmable Interrupt Controller, as you can see it's an interrupt controlling mechanism. It often causes errors (in windows too) and thus you may disable it.

What you can do is to install your ubuntu from the cd, and then, **before rebooting** perform the following steps:

1. press <ALT>+F2 keys and type in: [COLOR="Red"]xterm[/COLOR]

2. in the appearing window type: [COLOR="Red"]sudo fdisk -l[/COLOR]
You now have to find the partition where your ubuntu resides. the output of the command may look similar to this:
```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         892     7164958+   7  HPFS/NTFS
/dev/hda2             893        1866     7823655   83  Linux
/dev/hda3            1867        2840     7823655   83  Linux
/dev/hda4            2841        4865    16265812+   f  W95 Ext'd (LBA)
/dev/hda5            2841        4802    15759733+  83  Linux
/dev/hda6            4803        4865      506016   82  Linux swap / Solaris

```
(you might have just one linux partition, you can see it in the last column)
The first column indicates the device (e.g. /dev/hda2).

I presume that your device is /dev/hda2 (the linux partition, **not ** linux swap.

3. in the xterm window type: [COLOR="Red"]sudo mount /dev/hda2 /mnt[/COLOR] (or instead of hda2 whatever your partition is).

4. in the xterm window type: [COLOR="Red"]sudo gedit /mnt/boot/grub/menu.lst [/COLOR]

5. in the gedit editor find the part that looks similar to this:
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=7f744eca-334e-431b-8c51-48febd70103b ro elevator=cfq
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

```
(If you don't use a generic kernel, it may look different from here).

6. go to the **kernel** line (it may look different in your installation)

7. Add a space character and **noapic** at the end of this line
8. Save the file.
9. reboot
10. enjoy

Hope it can help

---

### Post by ElQuia on 2007-04-19
Hello. I have M2N4-SLI and when I try to install 7.04 I get APIC error. I´ve tried with 704 AMD DVD, 7.04 alternate amd, 7.04 i386 and 7.04 amd. The message is the same.

I tried ALL the bios available on asus page, from 301 to 902. It´s the same. Some user @asus page said that with bios 704 ubuntu worked.

THE PROBLEM IS THAT I CANT INSTALL, SETUP GIVES THE MESSAGE (SEE BELOW) AND FREEZES. SO I CANT EDIT MENU.LST.

I even tried an Mandriva (arghhhhh) live cd, it wont boot, it freezes

- MP-BIOS bug: 8254 timer not connected to IO-APIC.
- Kernel Panic - not syncing: IO-APIC + timer doesn´t work!. 
- HARDWARE ERROR. CPU0: Machine Check Exception. TSC 539c47cf42 ADDR 5bcf78. This is not a software problem. Kernel panic - not syncing: Machine Check
- Contact your hardware vendor.

PLEASSSEEEEEE somebody help: any suggestions: [email]elquianet@yahoo.com.ar[/email]

---

### Post by pross on 2007-04-20
perhaps you could have searched the forums first and seen my post about the m2n4-sli timer

[http://ubuntuforums.org/showthread.php?t=414200&highlight=m2n4-sli](http://ubuntuforums.org/showthread.php?t=414200&highlight=m2n4-sli)

---

### Post by ElQuia on 2007-04-20
I did read your post (after posting I must say). It´s not easy to find info in here :-D. :lolflag:

Let´s see: with no F6 parameters the error I get is:

"MP-BIOS bug: 8254 timer not connected to IO-APIC.
Kernel Panic - not syncing: IO-APIC + timer doesn´t work!. 
HARDWARE ERROR
CPU0: Machine Check Exception: 4 Bank 0: b653c00000000135
TSC 21d496f208 ADDR 5bcf78
This is not a software problem!
Run through mcelog --ascii to decode and contact your hardware vendor
Kernel panic - not syncing: Machine check"

If I pass the following parameters to F6 I get only:

"HARDWARE ERROR
CPU0: Machine Check Exception: 4 Bank 0: b653c00000000135
TSC 21d496f208 ADDR 5bcf78
This is not a software problem!
Run through mcelog --ascii to decode and contact your hardware vendor
Kernel panic - not syncing: Machine check"

Of course eveything freezes.
Its the same with alternate amd or amd.

I´m sort of a newbie in linux.... soooo PLEASEEEEEEEEEE HEEEEELP  :(

---

### Post by ElQuia on 2007-04-20
SORRY!!
I forgot: the parameters I passed to F6:

acpi=off noapic nolapic enable_8524_timer

I havn´t tried "acpi=noirq" as someone in here suggested.

Again: h e l p ?

---

### Post by pross on 2007-04-20
enable_8524_timer pci=biosirq <= thats what i use ..dont need noapic then

---

### Post by ElQuia on 2007-04-20
I´ll try only w/those parameters?
Non of the others? like acpi=off, acpi=noirq or nolapic?

I´m going to sleep so it will be later :-)

THANKSSSSS, hope it works.

---

### Post by pross on 2007-04-20
just enable_8524_timer pci=biosirq work 100% for me :)

---

### Post by ElQuia on 2007-04-20
Eyyyy:

With enable_8524_timer pci=biosirq

PCI: Unkown option "biosirq"

Ubuntu 7.04 final, AMD desktop and AMD Alternate, both give the same message....

Any suggestions? :confused:

:?:

---

### Post by pross on 2007-04-21
This is taken from my 'dmesg'

```

Kernel command line: root=UUID=d51b7fb1-b68c-4f65-8f38-f36d742d5c9d ro quiet splash enable_8524_timer pci=biosirq
```

here is the complete output:

```
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fde0000 end: 000000003fee0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fee0000 size: 0000000000003000 end: 000000003fee3000 type: 4
[    0.000000] copy_e820_map() start: 000000003fee3000 size: 000000000000d000 end: 000000003fef0000 type: 3
[    0.000000] copy_e820_map() start: 000000003fef0000 size: 0000000000010000 end: 000000003ff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fee0000 (usable)
[    0.000000]  BIOS-e820: 000000003fee0000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f53b0
[    0.000000] Entering add_active_range(0, 0, 261856) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261856
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261856
[    0.000000] On node 0 totalpages: 261856
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32227 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v002 Nvidia                                ) @ 0x000f6e80
[    0.000000] ACPI: XSDT (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x3fee30c0
[    0.000000] ACPI: FADT (v003 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x3feeb2c0
[    0.000000] ACPI: MCFG (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x3feeb4c0
[    0.000000] ACPI: MADT (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x3feeb400
[    0.000000] ACPI: DSDT (v001 NVIDIA ASUSACPI 0x00001000 MSFT 0x03000000) @ 0x00000000
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] Detected 2454.229 MHz processor.
[   23.719366] Built 1 zonelists.  Total pages: 259811
[   23.719369] Kernel command line: root=UUID=d51b7fb1-b68c-4f65-8f38-f36d742d5c9d ro quiet splash enable_8524_timer pci=biosirq
[   23.719480] mapped APIC to ffffd000 (fee00000)
[   23.719482] mapped IOAPIC to ffffc000 (fec00000)
[   23.719484] Enabling fast FPU save and restore... done.
[   23.719486] Enabling unmasked SIMD FPU exception support... done.
[   23.719491] Initializing CPU#0
[   23.719522] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   23.719567] spurious 8259A interrupt: IRQ7.
[   23.720666] Console: colour VGA+ 80x25
[   23.720943] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.721239] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.736597] Memory: 1026996k/1047424k available (1992k kernel code, 19724k reserved, 893k data, 328k init, 129920k highmem)
[   23.736605] virtual kernel memory layout:
[   23.736606]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   23.736607]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.736608]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.736609]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.736610]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   23.736611]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   23.736612]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   23.736614] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.815474] Calibrating delay using timer specific routine.. 4911.35 BogoMIPS (lpj=9822706)
[   23.815503] Security Framework v1.0.0 initialized
[   23.815509] SELinux:  Disabled at boot.
[   23.815520] Mount-cache hash table entries: 512
[   23.815616] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[   23.815622] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.815624] CPU: L2 Cache: 512K (64 bytes/line)
[   23.815626] CPU 0(2) -> Core 0
[   23.815628] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[   23.815636] Compat vDSO mapped to ffffe000.
[   23.815638] Remapping vsyscall page to ffffe000
[   23.815645] Checking 'hlt' instruction... OK.
[   23.831564] SMP alternatives: switching to UP code
[   23.831848] Early unpacking initramfs... done
[   24.066442] ACPI: Core revision 20060707
[   24.068661] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   24.072818] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   24.072832] SMP alternatives: switching to SMP code
[   24.072897] Booting processor 1/1 eip 3000
[   24.082109] Initializing CPU#1
[   24.162333] Calibrating delay using timer specific routine.. 4908.67 BogoMIPS (lpj=9817356)
[   24.162338] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[   24.162343] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.162345] CPU: L2 Cache: 512K (64 bytes/line)
[   24.162347] CPU 1(2) -> Core 1
[   24.162348] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[   24.163398] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   24.163406] Total of 2 processors activated (9820.03 BogoMIPS).
[   24.163535] ENABLING IO-APIC IRQs
[   24.163710] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   24.203399] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   24.203427] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   24.203428] ...trying to set up timer as Virtual Wire IRQ... failed.
[   24.243114] ...trying to set up timer as ExtINT IRQ... works.
[   24.487116] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had 475 usecs TSC skew, fixed it up.
[    0.000002] CPU#1 had -475 usecs TSC skew, fixed it up.
[    0.003997] Brought up 2 CPUs
[    0.057908] migration_cost=177
[    0.058086] Booting paravirtualized kernel on bare hardware
[    0.058130] Time: 11:56:27  Date: 03/21/107
[    0.058151] NET: Registered protocol family 16
[    0.058208] EISA bus registered
[    0.058210] ACPI: bus type pci registered
[    0.062596] PCI: PCI BIOS revision 3.00 entry at 0xf1fa0, last bus=5
[    0.062597] PCI: Using configuration type 1
[    0.062599] Setting up standard PCI resources
[    0.070388] ACPI: Interpreter enabled
[    0.070390] ACPI: Using IOAPIC for interrupt routing
[    0.070833] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.070837] PCI: Probing PCI hardware (bus 00)
[    0.072866] PCI: Transparent bridge - 0000:00:09.0
[    0.073055] Boot video device is 0000:05:00.0
[    0.073101] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.111586] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.115012] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.115291] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.115567] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.115845] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[    0.116129] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.116406] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.116684] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.116964] ACPI: PCI Interrupt Link [LMAC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.117241] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.117519] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.117797] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.118073] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.118353] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.118640] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.118927] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.119213] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.119527] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.119835] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.120148] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.120457] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.120695] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.121013] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.121330] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.121646] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.121966] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.122283] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.122600] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.122917] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.123235] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.123561] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.123886] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.124222] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[    0.124531] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.124538] pnp: PnP ACPI init
[    0.129603] pnp: PnP ACPI: found 11 devices
[    0.129606] PnPBIOS: Disabled by ACPI PNP
[    0.129644] PCI: Using ACPI for IRQ routing
[    0.129647] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.174709] NET: Registered protocol family 8
[    0.174710] NET: Registered protocol family 20
[    0.175063] pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
[    0.175065] pnp: 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.175067] pnp: 00:01: ioport range 0x4400-0x447f has been reserved
[    0.175069] pnp: 00:01: ioport range 0x4480-0x44ff could not be reserved
[    0.175072] pnp: 00:01: ioport range 0x4800-0x487f has been reserved
[    0.175074] pnp: 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.175270] PCI: Bridge: 0000:00:09.0
[    0.175271]   IO window: disabled.
[    0.175273]   MEM window: disabled.
[    0.175275]   PREFETCH window: disabled.
[    0.175277] PCI: Bridge: 0000:00:0b.0
[    0.175278]   IO window: disabled.
[    0.175280]   MEM window: disabled.
[    0.175282]   PREFETCH window: disabled.
[    0.175284] PCI: Bridge: 0000:00:0c.0
[    0.175285]   IO window: disabled.
[    0.175286]   MEM window: disabled.
[    0.175288]   PREFETCH window: disabled.
[    0.175292] PCI: Bridge: 0000:00:0d.0
[    0.175293]   IO window: a000-afff
[    0.175296]   MEM window: fb000000-fdffffff
[    0.175298]   PREFETCH window: d0000000-dfffffff
[    0.175300] PCI: Bridge: 0000:00:0e.0
[    0.175302]   IO window: 9000-9fff
[    0.175304]   MEM window: f8000000-faffffff
[    0.175306]   PREFETCH window: c0000000-cfffffff
[    0.175312] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    0.175318] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.175323] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.175328] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.175332] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.175358] NET: Registered protocol family 2
[    0.215926] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.216052] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.216681] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.217020] TCP: Hash tables configured (established 131072 bind 65536)
[    0.217022] TCP reno registered
[    0.231961] checking if image is initramfs... it is
[    0.694986] Freeing initrd memory: 7011k freed
[    1.292000] audit: initializing netlink socket (disabled)
[    1.292000] audit(1177156588.476:1): initialized
[    1.292000] highmem bounce pool size: 64 pages
[    1.292000] VFS: Disk quotas dquot_6.5.1
[    1.292000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.292000] io scheduler noop registered
[    1.292000] io scheduler anticipatory registered
[    1.292000] io scheduler deadline registered
[    1.292000] io scheduler cfq registered (default)
[    1.308000] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[    1.308000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    1.308000] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[    1.308000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    1.308000] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[    1.308000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    1.308000] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[    1.308000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    1.308000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    1.308000] assign_interrupt_mode Found MSI capability
[    1.308000] Allocate Port Service[0000:00:0b.0:pcie00]
[    1.308000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    1.308000] assign_interrupt_mode Found MSI capability
[    1.308000] Allocate Port Service[0000:00:0c.0:pcie00]
[    1.308000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    1.308000] assign_interrupt_mode Found MSI capability
[    1.308000] Allocate Port Service[0000:00:0d.0:pcie00]
[    1.308000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    1.308000] assign_interrupt_mode Found MSI capability
[    1.308000] Allocate Port Service[0000:00:0e.0:pcie00]
[    1.308000] isapnp: Scanning for PnP cards...
[    1.660000] isapnp: No Plug & Play device found
[    1.676000] Real Time Clock Driver v1.12ac
[    1.676000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.676000] mice: PS/2 mouse device common for all mice
[    1.676000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.676000] input: Macintosh mouse button emulation as /class/input/input0
[    1.676000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.676000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.676000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.676000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.676000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.676000] EISA: Probing bus 0 at eisa.0
[    1.676000] Cannot allocate resource for EISA slot 4
[    1.676000] EISA: Detected 0 cards.
[    1.708000] TCP cubic registered
[    1.708000] NET: Registered protocol family 1
[    1.708000] Starting balanced_irq
[    1.708000] Using IPI No-Shortcut mode
[    1.708000] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.708000] ACPI: (supports S0 S1 S3 S4 S5)
[    1.708000]   Magic number: 3:621:934
[    1.708000] Freeing unused kernel memory: 328k freed
[    1.712000] Time: acpi_pm clocksource has been installed.
[    2.888000] Capability LSM initialized
[    2.916000] ACPI: Fan [FAN] (on)
[    2.920000] ACPI: Thermal Zone [THRM] (40 C)
[    3.328000] usbcore: registered new interface driver usbfs
[    3.328000] usbcore: registered new interface driver hub
[    3.340000] usbcore: registered new device driver usb
[    3.340000] SCSI subsystem initialized
[    3.344000] libata version 2.20 loaded.
[    3.348000] sata_nv 0000:00:07.0: version 3.3
[    3.348000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    3.348000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 16
[    3.348000] sata_nv 0000:00:07.0: Using ADMA mode
[    3.348000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    3.348000] ata1: SATA max UDMA/133 cmd 0xf884a480 ctl 0xf884a4a0 bmdma 0x0001d400 irq 16
[    3.348000] ata2: SATA max UDMA/133 cmd 0xf884a580 ctl 0xf884a5a0 bmdma 0x0001d408 irq 16
[    3.348000] scsi0 : sata_nv
[    3.376000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[    3.376000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.660000] ata1: SATA link down (SStatus 0 SControl 300)
[    3.660000] scsi1 : sata_nv
[    3.976000] ata2: SATA link down (SStatus 0 SControl 300)
[    3.980000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    3.980000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 17
[    3.980000] sata_nv 0000:00:08.0: Using ADMA mode
[    3.980000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    3.980000] ata3: SATA max UDMA/133 cmd 0xf88a2480 ctl 0xf88a24a0 bmdma 0x0001c000 irq 17
[    3.980000] ata4: SATA max UDMA/133 cmd 0xf88a2580 ctl 0xf88a25a0 bmdma 0x0001c008 irq 17
[    3.980000] scsi2 : sata_nv
[    4.452000] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.468000] ata3.00: ata_hpa_resize 1: sectors = 321672960, hpa_sectors = 321672960
[    4.468000] ata3.00: ATA-7: ExcelStor Technology J8160S, P22OA50U, max UDMA/133
[    4.468000] ata3.00: 321672960 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    4.480000] ata3.00: ata_hpa_resize 1: sectors = 321672960, hpa_sectors = 321672960
[    4.480000] ata3.00: configured for UDMA/133
[    4.480000] scsi3 : sata_nv
[    4.792000] ata4: SATA link down (SStatus 0 SControl 300)
[    4.796000] scsi 2:0:0:0: Direct-Access     ATA      ExcelStor Techno P22O PQ: 0 ANSI: 5
[    4.796000] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[    4.796000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    4.796000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 18
[    4.796000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    4.796000] forcedeth: using HIGHDMA
[    4.804000] SCSI device sda: 321672960 512-byte hdwr sectors (164697 MB)
[    4.804000] sda: Write Protect is off
[    4.804000] sda: Mode Sense: 00 3a 00 00
[    4.804000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.804000] SCSI device sda: 321672960 512-byte hdwr sectors (164697 MB)
[    4.804000] sda: Write Protect is off
[    4.804000] sda: Mode Sense: 00 3a 00 00
[    4.804000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.804000]  sda: sda1
[    4.812000] sd 2:0:0:0: Attached scsi disk sda
[    4.816000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    5.320000] eth0: forcedeth.c: subsystem: 01043:812a bound to 0000:00:0a.0
[    5.320000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[    5.320000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 19
[    5.320000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    5.320000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    5.320000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    5.320000] ehci_hcd 0000:00:02.1: debug port 1
[    5.320000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    5.320000] ehci_hcd 0000:00:02.1: irq 19, io mem 0xfeb00000
[    5.320000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.320000] usb usb1: configuration #1 chosen from 1 choice
[    5.320000] hub 1-0:1.0: USB hub found
[    5.320000] hub 1-0:1.0: 10 ports detected
[    5.428000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    5.428000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[    5.428000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    5.428000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    5.428000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    5.428000] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfe02f000
[    5.488000] usb usb2: configuration #1 chosen from 1 choice
[    5.488000] hub 2-0:1.0: USB hub found
[    5.488000] hub 2-0:1.0: 10 ports detected
[    5.596000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[    5.596000] NFORCE-CK804: chipset revision 242
[    5.596000] NFORCE-CK804: not 100% native mode: will probe irqs later
[    5.596000] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[    5.596000]     ide0: BM-DMA at 0xe800-0xe807, BIOS settings: hda:DMA, hdb:DMA
[    5.596000]     ide1: BM-DMA at 0xe808-0xe80f, BIOS settings: hdc:DMA, hdd:DMA
[    5.596000] Probing IDE interface ide0...
[    5.888000] hda: ExcelStor Technology J840, ATA DISK drive
[    6.564000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    6.580000] Probing IDE interface ide1...
[    7.600000] hdd: TSSTcorpCD/DVDW SH-S182D, ATAPI CD/DVD-ROM drive
[    7.660000] ide1 at 0x170-0x177,0x376 on irq 15
[    7.668000] hda: max request size: 512KiB
[    7.668000] hda: 80418240 sectors (41174 MB) w/1719KiB Cache, CHS=16383/255/63, UDMA(133)
[    7.668000] hda: cache flushes supported
[    7.668000]  hda: hda1 hda2 hda3
[    7.696000] hdd: ATAPI 63X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.696000] Uniform CD-ROM driver Revision: 3.20
[    7.948000] Attempting manual resume
[    7.948000] swsusp: Resume From Partition 3:2
[    7.948000] PM: Checking swsusp image.
[    7.948000] PM: Resume from disk failed.
[    7.964000] kjournald starting.  Commit interval 5 seconds
[    7.964000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.896000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.900000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.948000] input: PC Speaker as /class/input/input2
[   17.044000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   17.044000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   17.064000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.200000] nvidia: module license 'NVIDIA' taints kernel.
[   17.452000] NET: Registered protocol family 17
[   17.476000] PCI: Enabling device 0000:04:00.0 (0000 -> 0003)
[   17.476000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   17.476000] ACPI: PCI Interrupt 0000:04:00.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
[   17.476000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   17.476000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   17.476000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[   17.476000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   17.476000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   17.620000] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   17.628000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   17.628000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   17.628000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.952000] intel8x0_measure_ac97_clock: measured 58758 usecs
[   17.952000] intel8x0: clocking to 47006
[   18.084000] fuse init (API version 7.8)
[   18.132000] lp: driver loaded but no devices found
[   18.156000] Adding 510968k swap on /dev/disk/by-uuid/f06d1cce-31ac-41b6-b584-67d8f5f2098c.  Priority:-1 extents:1 across:510968k
[   18.264000] EXT3 FS on hda3, internal journal
[   18.448000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   18.488000] NTFS volume version 3.1.
[   18.880000] NET: Registered protocol family 10
[   18.880000] lo: Disabled Privacy Extensions
[   19.124000] ibm_acpi: ec object not found
[   19.192000] No dock devices found.
[   19.216000] Using specific hotkey driver
[   19.300000] input: Power Button (FF) as /class/input/input4
[   19.300000] ACPI: Power Button (FF) [PWRF]
[   19.300000] input: Power Button (CM) as /class/input/input5
[   19.300000] ACPI: Power Button (CM) [PWRB]
[   19.360000] pcc_acpi: loading...
[   19.520000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   19.520000] powernow-k8: MP systems not supported by PSB BIOS structure
[   19.520000] powernow-k8: MP systems not supported by PSB BIOS structure
[   28.404000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 4:00.0] forgot to specify physical device; fix it!
[   28.404000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 4:00.0] forgot to specify physical device; fix it!
[   28.404000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 4:00.0] forgot to specify physical device; fix it!
[   28.760000] ppdev: user-space parallel port driver
[   29.028000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 5:00.0] forgot to specify physical device; fix it!
[   29.028000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 5:00.0] forgot to specify physical device; fix it!
[   29.028000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 5:00.0] forgot to specify physical device; fix it!
[   29.412000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   29.412000] apm: disabled - APM is not SMP safe.
[   29.644000] Bluetooth: Core ver 2.11
[   29.644000] NET: Registered protocol family 31
[   29.644000] Bluetooth: HCI device and connection manager initialized
[   29.644000] Bluetooth: HCI socket layer initialized
[   29.684000] Bluetooth: L2CAP ver 2.8
[   29.684000] Bluetooth: L2CAP socket layer initialized
[   30.068000] Bluetooth: RFCOMM socket layer initialized
[   30.068000] Bluetooth: RFCOMM TTY layer initialized
[   30.068000] Bluetooth: RFCOMM ver 1.8
[   40.256000] eth0: no IPv6 routers present
[   42.256000] NVRM: Xid (0005:00): 6, PE0002 0184 beef0201 00000054 dea18000 05000400
[   42.260000] NVRM: Xid (0005:00): 29,  L1 -> L0
[   42.260000] NVRM: Xid (0004:00): 29,  L1 -> L0
[   43.436000] cdrom: hdd: mrw address space DMA selected
[   43.672000] cdrom: hdd: mrw address space DMA selected
[   44.192000] ISO 9660 Extensions: Microsoft Joliet Level 1
[   44.420000] ISOFS: changing to secondary root

```

---

### Post by ElQuia on 2007-04-22
Hey Pross, I´m a newbie Linux user so I don´t know what dmesg is :-(
Sorry for badgerint, but can´t you suggest something easier?

BTW: what bios are you using on you mobo?, I tried all available with the same results... left it with 902 beta because all others had the same problem with ubuntu. 902 works ok with XP and Vista...

But I want my ubuntu!!!!!!!!!

Pleaseeeeeeee

---

### Post by pross on 2007-04-22
I'm using the latest bios too..

open a console...and type dmesg then hit return...it then spews out all the info from the kernel during bootup...
do you have plug'n'play bios enabled in the bios settings? i do
other than that i cant think of anything different in our setups until i see your dmesg..

---

### Post by ElQuia on 2007-04-22
Pross, the problem is I can´t install!!!!. Will dmesg run after install fails?

Remember I get:
- MP-BIOS bug: 8254 timer not connected to IO-APIC.
- Kernel Panic - not syncing: IO-APIC + timer doesn´t work!.
- HARDWARE ERROR. CPU0: Machine Check Exception. TSC 539c47cf42 ADDR 5bcf78. This is not a software problem. Kernel panic - not syncing: Machine Check
- Contact your hardware vendor.

---

### Post by ElQuia on 2007-04-22
plug'n'play bios, don´t remember. Am @work now, so tomorrow i´ll see to that and get back to you.

---

### Post by pross on 2007-04-22
ahh right...well i used noapic to install from the CD ..its documented on another thread...[http://ubuntuforums.org/showthread.php?t=414200&highlight=m2n4-sli](http://ubuntuforums.org/showthread.php?t=414200&highlight=m2n4-sli)

noapic got me up and running..but with no network and no xserver..i had to edit the xorg.conf and change to vesa

---

### Post by dalejefferson on 2007-04-24
Hmm all I did was remove quiet from the boot options!

Did not need any other mod.

---

### Post by Dyliak on 2007-08-31
Hi, I just followed the instruction wrote in this thread and I've been able to install correctly ubuntu (well that's kubuntu but is the same ;) ).

What's confusing is that:

1) I've to add noapic option for installing the first time the system.
2) I've to add enable_8524_timer pci=biosirq to kernel 2.6.20-15-generic and remove noapic
3) After updating to kernel 2.6.20-16-generic I had to remove enable_8524_timer pci=biosirq and also quiet (leaving only ro splash).

Now look like working correctly... well I haven't yet installed Nvidia driver for 8800 GT but I hope all will end happily now...

Hope to be helpful!

---

### Post by ViciousPotato on 2007-10-28
Bump.

I have an ASUS M2N4-SLI, updated to the 0902 BIOS (1202 didn't work either) and I keep getting the apic error.
When I use the boot option 'noapic', the loading screen with the orange bar comes up and 'loads' for about 5 minutes before throwing me into some shell thing? (I do not recall the exact name)
If I remove 'quiet' from the boot option, everything loads but when the actual desktop loads it comes up with irregularly coloured bars and dots where only the cursor is viewable.

Any help will be highly appreciated.
If you need more details, please don't hesitate to ask.

-ViciousPotato

---

### Post by dalejefferson on 2007-10-29
> **ViciousPotato said:**
> Bump.

I have an ASUS M2N4-SLI, updated to the 0902 BIOS (1202 didn't work either) and I keep getting the apic error.
When I use the boot option 'noapic', the loading screen with the orange bar comes up and 'loads' for about 5 minutes before throwing me into some shell thing? (I do not recall the exact name)
If I remove 'quiet' from the boot option, everything loads but when the actual desktop loads it comes up with irregularly coloured bars and dots where only the cursor is viewable.

Any help will be highly appreciated.
If you need more details, please don't hesitate to ask.

-ViciousPotato

Hi,

The apic error is a generic error message and nothing to do with this issue on this board.

I install from alternative cd and remove the quiet splash options from grub after the install. Works with Fiesty and Gutsy with 1202 bios.

I installed 3 of these motherboards last week so if you have a issue it maybe something else.

---

### Post by dalamar666 on 2007-10-29
I have that motherboard.  I installed Ubuntu 7.10 with the noapic option and it worked.  The only problem I am having is with the sound thing.  I am getting intermediate issues with the xine sound using the onboard sound.  With booting right to the shell command you may want to try using.

dpkg-reconfigure xserver-xorg

This may help fix the issue you are having.  It is what I have used when my ATI card screws things up.

---

### Post by ViciousPotato on 2007-10-29
> **dalejefferson said:**
> Hi,

The apic error is a generic error message and nothing to do with this issue on this board.

I install from alternative cd and remove the quiet splash options from grub after the install. Works with Fiesty and Gutsy with 1202 bios.

I installed 3 of these motherboards last week so if you have a issue it maybe something else.

Okay, wow, what a fun night.
I updated to the 1202 bios, installed using the alternative CD with the quiet option removed, all is (ok, was) going well.
I got up to partitioning my drive. Eep.

Currently, I have 2 SATA drives - 1 320gb, 1 500gb - in my system.
My 320gb, the one I want to install Ubuntu on, is split into three partitions.
One for XP (C:\), one for Ubuntu (U:\), one for storage. (D:\)

How on earth do I tell Ubuntu to install to the U:\ drive?
<snip> - Formatted to Linux Ext3.

---

### Post by ViciousPotato on 2007-10-29
Okay, I installed Ubuntu.
However, when I load it (removing quiet from boot options, too) it loads .. and loads .. then finally loads, however the screen goes a really weird colour.
It has a black background with white dots going diagonally across the screen and seems to flicker.
Graphics card is nVidia 7300GS, however I don't think it's related.

Edit: Cursor is viewable, movable, etc. and is the correct cursor.

Edit #2: Turns out my 22" monitor didn't like the resolution Ubuntu was trying to use ... works fine on my 17", shall configure it from there.

---

### Post by tonholis on 2007-11-21
hi people

I'm Brazilian, then sorry for the bad english...

I'm trying install ubuntu for weeks, and have not success
my hardware is:

M2N4 SLI
Athlon X2 4600+
2GB RAM Corsair
320GB HD Seagate SATA 2
XFX GeForce 8600GT Fatal1ty

the install stop on this:

[  683-840000] kjournald starting: Commit interval 5 seconds
[  683-840000] EXT3-fs: mounted filesystem with ordered data mode

anyone ideas?

---

