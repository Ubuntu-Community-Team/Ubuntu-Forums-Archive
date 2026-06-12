---
title: "hotplug &amp; USB failing"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by sperlyjinx on 2006-01-29
I've had 5.10 running on my system stably for several months.  Last week, I upgraded the kernel to 2.6.12-10 and have started having problems w/ hotplug.  Every other time I boot, the system hangs at "starting hotplug subsystem".  I've seen several simalar problems on this forum, but none of the solutions have worked for me.  Here is the relevant output from dmesg:
[4294767.026000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294767.026000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294767.158000] i2c-sis96x version 1.0.0
[4294767.162000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
[4294767.383000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[4294767.737000] AC'97 0 analog subsections not ready
[4294767.797000] intel8x0_measure_ac97_clock: measured 49290 usecs
[4294767.797000] intel8x0: clocking to 48000
[4294769.508000] Real Time Clock Driver v1.12
[4294769.596000] input: PC Speaker
[4294769.685000] Floppy drive(s): fd0 is 1.44M
[4294769.700000] FDC 0 is a post-1991 82077
[4294769.872000] ide-floppy driver 0.99.newide
[4294769.878000] hdf: No disk in drive
[4294769.879000] hdf: 244736kB, 239/64/32 CHS, 4096 kBps, 512 sector size, 2941 rpm
[4294770.519000] NET: Registered protocol family 17
[4294772.511000] eth0: Media Link On 100mbps full-duplex
[4294775.531000] NET: Registered protocol family 10
[4294775.531000] Disabled Privacy Extensions on device c031eb40(lo)
[4294775.532000] IPv6 over IPv4 tunneling driver
[4294776.424000] ACPI: Power Button (FF) [PWRF]
[4294776.424000] ACPI: Power Button (CM) [PWRB]
[4294776.520000] ibm_acpi: ec object not found
[4294777.530000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4294780.157000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294780.162000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294780.162000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294780.162000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294780.175000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294780.175000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294780.175000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294780.175000] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
[4294780.176000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294780.176000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4294780.177000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[4294780.177000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294780.186000] [fglrx] free  AGP = 54800384
[4294780.186000] [fglrx] max   AGP = 54800384
[4294780.186000] [fglrx] free  LFB = 116387840
[4294780.186000] [fglrx] max   LFB = 116387840
[4294780.186000] [fglrx] free  Inv = 0
[4294780.186000] [fglrx] max   Inv = 0
[4294780.186000] [fglrx] total Inv = 0
[4294780.186000] [fglrx] total TIM = 0
[4294780.186000] [fglrx] total FB  = 0
[4294780.186000] [fglrx] total AGP = 16384
[4294781.318000] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[4294781.318000] apm: overridden by ACPI.
[4294786.379000] eth0: no IPv6 routers present
[4294895.834000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4294911.865000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4294990.018000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4294992.022000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295064.162000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295230.488000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295237.987000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295264.556000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295380.563000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295561.880000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295561.886000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295767.641000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295769.551000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295779.858000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295831.673000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4295899.809000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296083.378000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296095.595000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296162.327000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296170.991000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296183.213000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296258.518000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296444.887000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296472.486000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296478.954000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296496.926000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296541.755000] APIC error on CPU0: 00(40)
[4296570.246000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296611.214000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296715.422000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296731.198000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296743.420000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4296938.972000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4297216.413000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4297250.480000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4297348.675000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4297350.679000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4297454.885000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4297591.155000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4297803.576000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4297911.792000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298192.351000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298230.427000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298320.161000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298332.383000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298344.605000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298372.709000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298543.048000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298645.251000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298793.545000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298827.613000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298894.603000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4298931.269000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4300984.707000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4300996.929000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301202.653000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301251.551000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301263.774000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301300.449000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301300.455000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301312.672000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301312.678000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301324.901000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301337.124000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301386.022000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301974.728000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4301999.180000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302023.632000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302023.638000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302035.861000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302512.185000] usb 3-4: new high speed USB device using ehci_hcd and address 2
[4302570.901000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302584.928000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302649.257000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302661.479000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302732.444000] ehci_hcd 0000:00:03.3: remove, state 1
[4302745.249000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302853.553000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302914.172000] APIC error on CPU0: 40(40)
[4302987.553000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4302999.777000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303012.001000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303030.077000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303036.448000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303048.671000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303060.894000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303073.117000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303134.236000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303146.459000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303158.682000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303170.905000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303219.797000] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[4303222.918000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4303222.918000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5

It is extremely annoying because my USB devices don't work anymore.  I've tried to downgrade back to 2.6.12-9, but now I have the same problem w/ that kernel.  As you can see, I also have this mysterious message regarding a couple of confused cdrom drives.  Any insight would be appreciated.

FYI, my system specs are:

ASUS P4SDX MOBO w/ Sis Chipset
2.66GHZ P4
1GB PC3200 RAM

Thanks in advance for your help!

-Sperly

---

### Post by sperlyjinx on 2006-01-30
Nevermind....

I just figured out that it is a hardware issue.  It was resolved by disabling the USB 2.0 functionality in my BIOS.  USB now works, albeit only at 1.1 speeds.

-Sperly

---

### Post by lorcat on 2006-07-04
[QUOTE=sperlyjinx]Nevermind....

I just figured out that it is a hardware issue.  It was resolved by disabling the USB 2.0 functionality in my BIOS.  USB now works, albeit only at 1.1 speeds.

-Sperly[/QUOTE]

Hi!
this problem I have still by now, but it's partly can be resolved by **irqpoll** parameter in kernel booting procedure, usb should be working just fine, as well as cdrom reading, but not burning.
I would also like to find someone to solve this kind of problem
this problem was a hell one in Breeze - had to compile my own kernel - 2.6.14, and a bit less annoying in Drake 2.6.15 kernel
regards

---

### Post by hanover.fiste on 2006-09-05
I started getting this once I added irqpoll to try to resolve a different issue. And for me, when this message appears on the console, the system locks up, as in it no longer responds even to network requests.

---

