---
title: "Kubuntu freezes when log off restart or shutdown"
date: 2008-07-28
forum: General Help
---

### Post by abrasax on 2008-07-28
Fujitsu siemens amilo la1703
via k8n890 integrated graphics chrome9 hc igp
This morning i decided to install my first linux (Kubuntu). It went very well. I installed it on a new partition ext2 and even created a swap partition. So now i have windows xp and kubuntu. Xp works fine. Kubuntu loads, i log in and first problem is that i cannot set the resolution i want. Some error when i try to open display and monitor settings. Resolution is set to god knows what so taskbar is below the edge of the display and windows open to the right of it. Next more serious problem is that i cannot log off restart or shutdown without pressing the power button for 6-7 seconds. And that is not good. every time i do that kubuntu fails to load. i then have to run fsck and press 'y' quite a lot then reboot and then it loads again. But last time the mouse stopped working.
So my question is:
Can something be done about it or will i have to find another distribution of linux or worse, give it up for good?

PS
sorry i wrote so much text. :)
Thanks in advance
And, i almost forgot i'm a complete noob when it comes to linux so be very descriptive. :)

---

### Post by kuja on 2008-07-28
After a bit of googling, it looks like that particular graphics chip isn't supported very well by Linux. 

Here are a couple of related links ... Maybe they'll prove useful, but I'm not sure that it'll solve the problem or not: 
[http://ubuntuforums.org/showthread.php?t=514248](http://ubuntuforums.org/showthread.php?t=514248)
[http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)

-----------------------------------------------------------------------------------------

Here are a couple things that might be worth trying, though I'm not sure at all if they'll be useful as I don't have a computer with a via graphics chip.

[color=red]Note: none of the below are 100% what you would have ... could vary based on what you need and what you have already in the /etc/X11/xorg.conf file (which is what the things below pertain to), as thus, none of the below is copy+pastable (probably). [/color]

To open that file for editing:

(in the gui), hit alt+f2 and a little box will come up (ie: run command), type ```
kdesudo kate /etc/X11/xorg.conf
``` 

(or in a console) ```
sudo editor /etc/X11/xorg.conf
``` (Note: editor is not begging to be replaced, it will use whatever alternative you have set (settable with the command update-alternatives), I think it defaults to nano.)


1) Try explicitly setting the driver to "**via**", failing this, try "**vesa**"
```

Section "Device"
Identifier "Via Chrome9"
Driver "via"
EndSection
```

2) Try setting the modes like in the example in the first link.
```
Section "Screen"
Identifier "Default Screen"
Device "Via Chrome9"
Monitor "Monitor1"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes "1024x768" "1280x1024" #Note, this is where you put the resolutions you want to have available for X
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "1280x1024" #See above note
EndSubSection
EndSection
```


Anyhow, I wish you luck.

---

### Post by abrasax on 2008-07-28
Question:
These links (thank you very much for these) are for graphics only. How can i be sure that this will fix restart/shutdown problem? I don't want to turn it off manually again.

---

### Post by kuja on 2008-07-28
> **abrasax said:**
> Question:
These links (thank you very much for these) are for graphics only. How can i be sure that this will fix restart/shutdown problem? I don't want to turn it off manually again.

A lot of the time that's actually a graphics driver problem. I have a feeling if you fix one problem it might fix both.

---

### Post by abrasax on 2008-07-28
OK. First I have to install kubuntu again because mouse stopped working last time i had to pull the plug. I'll try your fix and if that doesn't work i'll try the second link. It looks promising. Hope I will not have to restart :)
I'll let you know if I succeed and cry if I don't.

---

### Post by abrasax on 2008-07-29
Ok. Installed it again. Tried everything. Nothing works. Everytime no matter what i do or how i log out it freezes. Don't know what to do. I even tried to disable the splash screen which helped users who have the exact same problem like me. not working. Any suggestions?

---

### Post by caljohnsmith on 2008-07-29
Abrasax, I would check your system logs for errors (System > Admin > System Log). That will probably give a clue as to your shutdown problems. And please post the output of /var/log/syslog so we can take a look.

---

### Post by abrasax on 2008-07-29
ok .now it's too late for that. I used partition magic from windows and deleted the linux partitions. And then used windows recovery mode to disable grub. Now i'm back with windows. So until someone fixes this for good i'm going to use knoppix which has no problems. By the way i tried ubuntu live and it crashes in the same manner. I'm giving up for now. But i'll be back when i figure out how to use the terminal :)
while googling i found that everyone with this laptop (and many other) have the same problem.
Anyway thank you for trying to help me. Maybe i'll try another linux. Could you recommend?


i never gave up on anything that has to do with computers, so i will not give up now. I'll keep trying. I'll start by installing kubuntu again. i'll post logs as soon as i can. Be back soon.

---

### Post by caljohnsmith on 2008-07-29
Since you like KDE (and I do too), I would recommend trying Mandriva first, and PCLinuxOS second. If you like Kubuntu I think you will feel right at home with Mandriva, but if that doesn't work, you can give PCLinuxOS a try which is quite similar. That's great if you want to try and troubleshoot Kubuntu some more and try and get it working, but if another good distro like Mandriva works "out-of-the-box", maybe it's worth it to just go with it for now? ;)

---

### Post by abrasax on 2008-07-29
OK. I decided not to install it. Is it possible to do all that on live Kubuntu? I mean, to fix those problems. Here's a system log from the livecd:

07/29/2008 07:55:43 PM	ubuntu	avahi-daemon[8003]	Registering new address record for fe80::2a0:d1ff:fec9:96a4 on eth0.*.

07/29/2008 07:55:52 PM	ubuntu	kernel	[  136.062263] eth0: no IPv6 routers present

07/29/2008 07:56:16 PM	ubuntu	kernel	[  373.964848] hda-intel: Invalid position buffer, using LPIB read method instead.

07/29/2008 07:56:37 PM	ubuntu	NetworkManager	<info>  Updating allowed wireless network lists. 

07/29/2008 07:56:37 PM	ubuntu	NetworkManager	<WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks. 

07/29/2008 08:15:08 PM	ubuntu	none	-- MARK --

07/30/2008 11:55:04 PM	ubuntu	syslogd 1.5.0#1ubuntu1	restart.

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]     0:        0 ->   229008

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] 0MB HIGHMEM available.

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] 894MB LOWMEM available.

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: APIC 37E96E1C, 0066 (r1 PTLTD  ^I APIC    6040000  LTP        0)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: DMI detected: Fujitsu Siemens

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: DSDT 37E92EAC, 3EFC (r1 IEC___ E25_____  6040000 MSFT  100000E)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: FACP 37E96DA8, 0074 (r1 AMDK8  PTLTW     6040000 PTL_    F4240)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: FACS 37E97FC0, 0040

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfecc0000] gsi_base[24])

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: IRQ0 used by override.

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: IRQ2 used by override.

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: IRQ9 used by override.

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: Local APIC address 0xfee00000

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: MCFG 37E96E82, 003C (r1 PTLTD    MCFG    6040000  LTP        0)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: PM-Timer IO Port: 0x4008

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: RSDP 000F8710, 0014 (r0 PTLTD )

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: RSDP signature @ 0xC00F8710 checksum 0

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: RSDT 37E92E78, 0034 (r1 FSC    PC        6040000  LTP        0)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] ACPI: SSDT 37E96EBE, 0142 (r1 PTLTD  POWERNOW  6040000  LTP        1)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037e90000 (usable)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 0000000037e90000 - 0000000037e97000 (ACPI data)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 0000000037e97000 - 0000000037f00000 (ACPI NVS)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] BIOS-provided physical RAM map:

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227219

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Detected 2000.114 MHz processor.

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]   DMA             0 ->     4096

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]   DMA zone: 0 pages reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]   DMA zone: 32 pages used for memmap

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]   DMA zone: 4064 pages, LIFO batch:0

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] DMI present.

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] early_node_map[1] active PFN ranges

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Enabling fast FPU save and restore... done.

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Enabling unmasked SIMD FPU exception support... done.

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Entering add_active_range(0, 0, 229008) 0 entries of 256 used

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] found SMP MP-table at 000f87d0

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]   HighMem    229008 ->   229008

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]   HighMem zone: 0 pages used for memmap

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Initializing cgroup subsys cpu

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Initializing cgroup subsys cpuset

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Initializing CPU#0

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] IOAPIC[1]: apic_id 2, version 3, address 0xfecc0000, GSI 24-47

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] mapped APIC to ffffb000 (fee00000)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] mapped IOAPIC to ffff9000 (fecc0000)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] mapped IOAPIC to ffffa000 (fec00000)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]   Movable zone: 0 pages used for memmap

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Movable zone start PFN for each node

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]   Normal       4096 ->   229008

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]   Normal zone: 1757 pages used for memmap

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000]   Normal zone: 223155 pages, LIFO batch:31

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] On node 0 totalpages: 229008

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Processor #0 15:12 APIC version 16

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Using ACPI (MADT) for SMP configuration information

07/30/2008 11:55:05 PM	ubuntu	kernel	[    0.000000] Zone PFN ranges:

07/30/2008 11:55:05 PM	ubuntu	kernel	[  101.393291] ip_tables: (C) 2000-2006 Netfilter Core Team

07/30/2008 11:55:05 PM	ubuntu	kernel	[  105.099704] No dock devices found.

07/30/2008 11:55:05 PM	ubuntu	kernel	[  106.210630] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3600+ processors (1 cpu cores) (version 2.20.00)

07/30/2008 11:55:05 PM	ubuntu	kernel	[  106.210676] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xe

07/30/2008 11:55:05 PM	ubuntu	kernel	[  106.210678] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x10

07/30/2008 11:55:05 PM	ubuntu	kernel	[  106.210681] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x12

07/30/2008 11:55:05 PM	ubuntu	kernel	[  106.210683] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.155687] Console: colour VGA+ 80x25

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.155690] console [tty0] enabled

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.156026] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.156642] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171468] Memory: 895356k/916032k available (2177k kernel code, 20044k reserved, 1006k data, 368k init, 0k highmem)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171475] virtual kernel memory layout:

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171476]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171477]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171479]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171480]     lowmem  : 0xc0000000 - 0xf7e90000   ( 894 MB)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171481]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171482]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171483]       .text : 0xc0100000 - 0xc0320434   (2177 kB)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171486] Checking if this processor honours the WP bit even in supervisor mode... Ok.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.171515] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251389] Calibrating delay using timer specific routine.. 4004.29 BogoMIPS (lpj=8008590)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251410] Security Framework initialized

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251414] SELinux:  Disabled at boot.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251426] AppArmor: AppArmor initialized

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251429] Failure registering capabilities with primary security module.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251436] Mount-cache hash table entries: 512

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251524] Initializing cgroup subsys ns

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251527] Initializing cgroup subsys cpuacct

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251535] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019 00000000

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251543] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251545] CPU: L2 Cache: 256K (64 bytes/line)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251547] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 00000019 00000000

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251555] Compat vDSO mapped to ffffe000.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.251563] Checking 'hlt' instruction... OK.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.267607] SMP alternatives: switching to UP code

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.268677] Freeing SMP alternatives: 11k freed

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.268787] Early unpacking initramfs... done

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.592483] ACPI: Core revision 20070126

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.592537] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.597288] CPU0: AMD Mobile AMD Sempron(tm) Processor 3600+ stepping 02

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.597307] Total of 1 processors activated (4004.29 BogoMIPS).

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.597864] ENABLING IO-APIC IRQs

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.598170] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.742522] Brought up 1 CPUs

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.742562] CPU0 attaching sched-domain:

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.742565]  domain 0: span 01

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.742566]   groups: 01

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.742713] net_namespace: 64 bytes

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.742719] Booting paravirtualized kernel on bare hardware

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.743131] Time: 23:53:53  Date: 07/30/08

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.743152] NET: Registered protocol family 16

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.743303] EISA bus registered

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.743331] ACPI: bus type pci registered

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.755953] PCI: BIOS BUG #81[49435000] found

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.756000] PCI: Using configuration type 1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.756007] Setting up standard PCI resources

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.757350] ACPI: EC: Look up EC in DSDT

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.958107] ACPI: Interpreter enabled

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.958110] ACPI: (supports S0 S3 S4 S5)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.958119] ACPI: Using IOAPIC for interrupt routing

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.963182] ACPI: EC: non-query interrupt received, switching to interrupt mode

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.973148] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.973151] ACPI: EC: driver started in interrupt mode

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.973187] ACPI: PCI Root Bridge [PCI0] (0000:00)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.974570] PCI: Transparent bridge - 0000:00:13.1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.974600] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.974754] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2PE._PRT]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.984587] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.984653] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *11, disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.984714] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *7, disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.984774] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0, disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.984856] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 9 *10 11 12)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.984933] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 9 10 *11 12)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985007] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 9 10 11 12) *7

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985071] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 9 10 11 12) *0, disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985136] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 9 10 11 12) *0, disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985203] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 9 10 11 12) *0, disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985268] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 9 10 11 12) *0, disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985344] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 9 10 11 12)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985440] ACPI: Power Resource [FAN0] (off)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985464] ACPI: Power Resource [FAN1] (off)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985502] Linux Plug and Play Support v0.97 (c) Adam Belay

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985528] pnp: PnP ACPI init

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.985535] ACPI: bus type pnp registered

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.987223] pnp: PnP ACPI: found 9 devices

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.987226] ACPI: ACPI bus type pnp unregistered

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.987229] PnPBIOS: Disabled by ACPI PNP

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.987406] PCI: Using ACPI for IRQ routing

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.987409] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.998027] NET: Registered protocol family 8

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.998029] NET: Registered protocol family 20

07/30/2008 11:55:05 PM	ubuntu	kernel	[   34.998084] AppArmor: AppArmor Filesystem Enabled

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.001999] Time: tsc clocksource has been installed.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010017] system 00:05: iomem range 0xfff00000-0xffffffff could not be reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010020] system 00:05: iomem range 0xffee0000-0xffefffff has been reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010023] system 00:05: iomem range 0xfec00000-0xfec00fff could not be reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010026] system 00:05: iomem range 0xfee00000-0xfee00fff could not be reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010028] system 00:05: iomem range 0xe0000000-0xefffffff could not be reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010033] system 00:06: ioport range 0x4d0-0x4d1 has been reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010036] system 00:06: ioport range 0x200-0x20f has been reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010038] system 00:06: ioport range 0x400-0x40f has been reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010041] system 00:06: ioport range 0xfe00-0xfe00 has been reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010044] system 00:06: ioport range 0x4000-0x407f has been reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.010046] system 00:06: ioport range 0x4100-0x411f has been reserved

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040328] PCI: Failed to allocate mem resource #6:10000@d0000000 for 0000:01:00.0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040330] PCI: Bridge: 0000:00:01.0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040332]   IO window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040336]   MEM window: d8000000-d8ffffff

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040339]   PREFETCH window: c0000000-cfffffff

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040343] PCI: Bridge: 0000:00:02.0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040344]   IO window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040348]   MEM window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040351]   PREFETCH window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040355] PCI: Bridge: 0000:00:03.0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040356]   IO window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040360]   MEM window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040363]   PREFETCH window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040368] PCI: Bridge: 0000:00:13.0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040369]   IO window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040373]   MEM window: d9000000-d90fffff

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040375]   PREFETCH window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040379] PCI: Bridge: 0000:00:13.1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040380]   IO window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040384]   MEM window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040387]   PREFETCH window: disabled.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040405] PCI: Setting latency timer of device 0000:00:01.0 to 64

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040420] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 16

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040425] PCI: Setting latency timer of device 0000:00:02.0 to 64

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040438] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 17

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040443] PCI: Setting latency timer of device 0000:00:03.0 to 64

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040453] PCI: Setting latency timer of device 0000:00:13.0 to 64

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040463] PCI: Setting latency timer of device 0000:00:13.1 to 64

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.040475] NET: Registered protocol family 2

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.077924] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.078182] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.079062] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.079499] TCP: Hash tables configured (established 131072 bind 65536)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.079503] TCP reno registered

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.089962] checking if image is initramfs... it is

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.541000] Switched to high resolution mode on CPU 0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.716811] Freeing initrd memory: 7939k freed

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.717331] audit: initializing netlink socket (disabled)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.717343] audit(1217462033.444:1): initialized

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.718896] VFS: Disk quotas dquot_6.5.1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.718957] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719073] io scheduler noop registered

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719075] io scheduler anticipatory registered

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719077] io scheduler deadline registered

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719085] io scheduler cfq registered (default)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719097] PCI: VIA PCI bridge detected. Disabling DAC.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719166] Boot video device is 0000:01:00.0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719267] PCI: Setting latency timer of device 0000:00:02.0 to 64

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719302] assign_interrupt_mode Found MSI capability

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719342] Allocate Port Service[0000:00:02.0:pcie00]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719377] Allocate Port Service[0000:00:02.0:pcie02]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719442] PCI: Setting latency timer of device 0000:00:03.0 to 64

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719480] assign_interrupt_mode Found MSI capability

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719523] Allocate Port Service[0000:00:03.0:pcie00]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719549] Allocate Port Service[0000:00:03.0:pcie02]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   35.719752] isapnp: Scanning for PnP cards...

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.073235] isapnp: No Plug & Play device found

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.096783] Real Time Clock Driver v1.12ac

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.096865] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.097780] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.097846] input: Macintosh mouse button emulation as /devices/virtual/input/input0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.097922] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.103230] i8042.c: Detected active multiplexing controller, rev 1.1.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.107588] serio: i8042 KBD port at 0x60,0x64 irq 1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.107592] serio: i8042 AUX0 port at 0x60,0x64 irq 12

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.107594] serio: i8042 AUX1 port at 0x60,0x64 irq 12

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.107597] serio: i8042 AUX2 port at 0x60,0x64 irq 12

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.107599] serio: i8042 AUX3 port at 0x60,0x64 irq 12

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.115857] mice: PS/2 mouse device common for all mice

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.115959] EISA: Probing bus 0 at eisa.0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.115978] Cannot allocate resource for EISA slot 4

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.115996] EISA: Detected 0 cards.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.115999] cpuidle: using governor ladder

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.116001] cpuidle: using governor menu

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.116078] NET: Registered protocol family 1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.116101] Using IPI No-Shortcut mode

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.116128] registered taskstats version 1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.116223]   Magic number: 0:43:910

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.116300]   hash matches device ptyz6

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.116370] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.116372] EDD information not available.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.116589] Freeing unused kernel memory: 368k freed

07/30/2008 11:55:05 PM	ubuntu	kernel	[   36.159743] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.393731] fuse init (API version 7.9)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.408747] ACPI: Transitioning device [FND0] to D3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.408751] ACPI: Transitioning device [FND0] to D3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.408754] ACPI: Fan [FND0] (off)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.408793] ACPI: Transitioning device [FND1] to D3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.408794] ACPI: Transitioning device [FND1] to D3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.408797] ACPI: Fan [FND1] (off)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.414686] ACPI: CPU0 (power states: C1[C1] C2[C2])

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.414692] ACPI: Processor [CPU0] (supports 16 throttling states)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.414704] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   37.416779] ACPI: Thermal Zone [THRM] (65 C)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.152319] SCSI subsystem initialized

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.201204] libata version 3.00 loaded.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.207801] usbcore: registered new interface driver usbfs

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.207821] usbcore: registered new interface driver hub

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.231803] usbcore: registered new device driver usb

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.239773] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 18

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.239821] ACPI: PCI interrupt for device 0000:00:0f.0 disabled

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.255397] sata_via 0000:00:0f.0: version 2.3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.255411] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 18

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.255446] sata_via 0000:00:0f.0: routed to hard irq line 11

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.266052] scsi0 : sata_via

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.286555] scsi1 : sata_via

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.286597] ata1: SATA max UDMA/133 cmd 0x4cb0 ctl 0x4ca4 bmdma 0x4c80 irq 18

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.286600] ata2: SATA max UDMA/133 cmd 0x4ca8 ctl 0x4ca0 bmdma 0x4c88 irq 18

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.292108] USB Universal Host Controller Interface driver v3.0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.321920] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.487192] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.920830] ata1.00: ATA-8: WDC WD1200BEVS-22UST0, 01.01A01, max UDMA/133

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.920834] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   38.935261] ata1.00: configured for UDMA/133

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.137910] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.148550] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-2 01.0 PQ: 0 ANSI: 5

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.148698] pata_via 0000:00:0f.1: version 0.3.3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.149545] scsi2 : pata_via

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.149954] scsi3 : pata_via

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.150463] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4c90 irq 14

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.150466] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4c98 irq 15

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.155504] Driver 'sd' needs updating - please use bus_type methods

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.155577] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.155587] sd 0:0:0:0: [sda] Write Protect is off

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.155590] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.155602] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.155639] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.155646] sd 0:0:0:0: [sda] Write Protect is off

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.155648] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.155659] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.155663]  sda: sda1 sda2 < sda5 sda6 >

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.291820] sd 0:0:0:0: [sda] Attached SCSI disk

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.297189] sd 0:0:0:0: Attached scsi generic sg0 type 0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.625341] ata4.00: ATAPI: Optiarc DVD RW AD-7540A, 1.42, max UDMA/33

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.796878] ata4.00: configured for UDMA/33

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.799325] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7540A  1.42 PQ: 0 ANSI: 5

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.799389] scsi 3:0:0:0: Attached scsi generic sg1 type 5

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.799524] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 19

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.799533] uhci_hcd 0000:00:10.0: UHCI Host Controller

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.799765] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.799794] uhci_hcd 0000:00:10.0: irq 19, io base 0x00004c00

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.799908] usb usb1: configuration #1 chosen from 1 choice

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.799927] hub 1-0:1.0: USB hub found

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.799932] hub 1-0:1.0: 2 ports detected

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.807394] Driver 'sr' needs updating - please use bus_type methods

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.808821] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.808826] Uniform CD-ROM driver Revision: 3.20

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.808873] sr 3:0:0:0: Attached scsi CD-ROM sr0

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.900517] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 20

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.900528] uhci_hcd 0000:00:10.1: UHCI Host Controller

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.900548] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.900576] uhci_hcd 0000:00:10.1: irq 20, io base 0x00004c20

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.900667] usb usb2: configuration #1 chosen from 1 choice

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.900688] hub 2-0:1.0: USB hub found

07/30/2008 11:55:05 PM	ubuntu	kernel	[   39.900692] hub 2-0:1.0: 2 ports detected

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.004296] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 18

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.004306] uhci_hcd 0000:00:10.2: UHCI Host Controller

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.004325] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.004345] uhci_hcd 0000:00:10.2: irq 18, io base 0x00004c40

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.004440] usb usb3: configuration #1 chosen from 1 choice

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.004458] hub 3-0:1.0: USB hub found

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.004462] hub 3-0:1.0: 2 ports detected

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.108096] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 21

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.108107] uhci_hcd 0000:00:10.3: UHCI Host Controller

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.108133] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.108160] uhci_hcd 0000:00:10.3: irq 21, io base 0x00004c60

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.108254] usb usb4: configuration #1 chosen from 1 choice

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.108272] hub 4-0:1.0: USB hub found

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.108276] hub 4-0:1.0: 2 ports detected

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.212733] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 21

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.216865] eth0: VIA Rhine II at 0xd9300400, 00:a0:d1:c9:96:a4, IRQ 21.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.217573] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.217800] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 18

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.217809] ehci_hcd 0000:00:10.4: EHCI Host Controller

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.217836] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.217869] ehci_hcd 0000:00:10.4: irq 18, io mem 0xd9300000

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.227774] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.227886] usb usb5: configuration #1 chosen from 1 choice

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.227906] hub 5-0:1.0: USB hub found

07/30/2008 11:55:05 PM	ubuntu	kernel	[   40.227912] hub 5-0:1.0: 8 ports detected

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.255167] ISO 9660 Extensions: Microsoft Joliet Level 3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.309498] ISO 9660 Extensions: RRIP_1991A

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.413466] usb 5-5: new high speed USB device using ehci_hcd and address 3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.545630] usb 5-5: configuration #1 chosen from 1 choice

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.646836] Registering unionfs 1.4

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.646840] unionfs: debugging is not enabled

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.656729] loop: module loaded

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.784733] usb 2-1: new low speed USB device using uhci_hcd and address 2

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.957799] usb 2-1: configuration #1 chosen from 1 choice

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.983807] usbcore: registered new interface driver hiddev

07/30/2008 11:55:05 PM	ubuntu	kernel	[   41.997795] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input2

07/30/2008 11:55:05 PM	ubuntu	kernel	[   42.008319] input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:10.1-1

07/30/2008 11:55:05 PM	ubuntu	kernel	[   42.008333] usbcore: registered new interface driver usbhid

07/30/2008 11:55:05 PM	ubuntu	kernel	[   42.008337] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

07/30/2008 11:55:05 PM	ubuntu	kernel	[   42.026821] squashfs: version 3.3 (2007/10/31) Phillip Lougher

07/30/2008 11:55:05 PM	ubuntu	kernel	[   92.868749] input: PC Speaker as /devices/platform/pcspkr/input/input3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   93.596551] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

07/30/2008 11:55:05 PM	ubuntu	kernel	[   93.846882] Linux agpgart interface v0.102

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.302059] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.552772] ACPI: AC Adapter [ADP0] (on-line)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.709269] input: Power Button (FF) as /devices/virtual/input/input4

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.741146] ACPI: Power Button (FF) [PWRF]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.741201] input: Power Button (CM) as /devices/virtual/input/input5

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.765150] ACPI: Power Button (CM) [PWRB]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.765207] input: Sleep Button (CM) as /devices/virtual/input/input6

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.793042] ACPI: Sleep Button (CM) [SLPB]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.793096] input: Lid Switch as /devices/virtual/input/input7

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.805038] agpgart: Detected VIA VT3336 chipset

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.808832] agpgart: AGP aperture is 128M @ 0xd0000000

07/30/2008 11:55:05 PM	ubuntu	kernel	[   94.809189] ACPI: Lid Switch [LID]

07/30/2008 11:55:05 PM	ubuntu	kernel	[   95.617133] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04753/0x200000

07/30/2008 11:55:05 PM	ubuntu	kernel	[   95.654405] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8

07/30/2008 11:55:05 PM	ubuntu	kernel	[   95.872961] ACPI: Battery Slot [BAT0] (battery present)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   95.876931] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:14/LNXVIDEO:00/input/input9

07/30/2008 11:55:05 PM	ubuntu	kernel	[   95.898904] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

07/30/2008 11:55:05 PM	ubuntu	kernel	[   96.556457] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 22

07/30/2008 11:55:05 PM	ubuntu	kernel	[   96.556486] PCI: Setting latency timer of device 0000:04:01.0 to 64

07/30/2008 11:55:05 PM	ubuntu	kernel	[   99.330390] device-mapper: uevent: version 1.0.3

07/30/2008 11:55:05 PM	ubuntu	kernel	[   99.330417] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]

07/30/2008 11:55:05 PM	ubuntu	kernel	Inspecting /boot/System.map-2.6.24-19-generic

07/30/2008 11:55:05 PM	ubuntu	kernel	Loaded 14818 symbols from 82 modules.

07/30/2008 11:55:05 PM	ubuntu	kernel	Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.

07/30/2008 11:55:05 PM	ubuntu	kernel	Symbols match kernel version 2.6.24.

07/30/2008 11:55:07 PM	ubuntu	NetworkManager	<info>  starting... 

07/30/2008 11:55:10 PM	ubuntu	kdm[7982]	StartServerSucces

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8003]	avahi-daemon 0.6.22 starting up.

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8003]	Failed to open /etc/resolv.conf: Invalid argument

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8003]	Found user 'avahi' (UID 107) and group 'avahi' (GID 116).

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8003]	Network interface enumeration completed.

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8003]	No service file found in /etc/avahi/services.

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8003]	Registering HINFO record with values 'I686'/'LINUX'.

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8003]	Server startup complete. Host name is ubuntu.local. Local service cookie is 2802254424.

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8003]	Successfully called chroot().

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8003]	Successfully dropped remaining capabilities.

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8003]	Successfully dropped root privileges.

07/30/2008 11:55:11 PM	ubuntu	avahi-daemon[8004]	chroot.c: open() failed: No such file or directory

07/30/2008 11:55:11 PM	ubuntu	kernel	[  113.368371] apm: BIOS not found.

07/30/2008 11:55:14 PM	ubuntu	kernel	[  115.807903] lp: driver loaded but no devices found

07/30/2008 11:55:14 PM	ubuntu	kernel	[  115.923678] ppdev: user-space parallel port driver

07/30/2008 11:55:17 PM	ubuntu	kernel	[  118.435865] [drm] Initialized drm 1.1.0 20060810

07/30/2008 11:55:17 PM	ubuntu	kernel	[  118.493167] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 23

07/30/2008 11:55:17 PM	ubuntu	kernel	[  118.493295] [drm] Initialized via 2.11.1 20070202 on minor 0

07/30/2008 11:55:17 PM	ubuntu	kernel	[  118.578022] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.

07/30/2008 11:55:17 PM	ubuntu	kernel	[  118.578047] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode

07/30/2008 11:55:17 PM	ubuntu	kernel	[  118.578133] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

07/30/2008 11:55:20 PM	ubuntu	dhcdbd	Started up.

07/30/2008 11:55:20 PM	ubuntu	kernel	[  152.409869] Marking TSC unstable due to: cpufreq changes.

07/30/2008 11:55:20 PM	ubuntu	kernel	[  152.414633] Time: acpi_pm clocksource has been installed.

07/30/2008 11:55:20 PM	ubuntu	kernel	[  152.897909] Clocksource tsc unstable (delta = -97758172 ns)

07/30/2008 11:55:20 PM	ubuntu	python	Writing graphics card hardware list to /var/lib/guidance/guidance-gfxhardware-snapshot

07/30/2008 11:55:29 PM	ubuntu	dhcdbd	message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason

07/30/2008 11:55:29 PM	ubuntu	kernel	[  315.169056] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<debug> [1217462129.059577] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7540A'). 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Activation (eth0) started... 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Deactivating device eth0. 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Device eth0 activation scheduled... 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  eth0: Device is fully-supported using driver 'via-rhine'. 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  nm_device_init(): device's worker thread started, continuing. 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  nm_device_init(): waiting for device's worker thread to start 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Now managing wired Ethernet (802.3) device 'eth0'. 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  SWITCH: no current connection, found better connection 'eth0'. 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Will activate connection 'eth0'. 

07/30/2008 11:55:29 PM	ubuntu	NetworkManager	<info>  Will activate wired connection 'eth0' because it now has a link. 

07/30/2008 11:55:30 PM	ubuntu	hcid[8414]	Bluetooth HCI daemon

07/30/2008 11:55:30 PM	ubuntu	hcid[8414]	Starting SDP server

07/30/2008 11:55:30 PM	ubuntu	kernel	[  316.580189] Bluetooth: Core ver 2.11

07/30/2008 11:55:30 PM	ubuntu	kernel	[  316.581461] NET: Registered protocol family 31

07/30/2008 11:55:30 PM	ubuntu	kernel	[  316.581472] Bluetooth: HCI device and connection manager initialized

07/30/2008 11:55:30 PM	ubuntu	kernel	[  316.581481] Bluetooth: HCI socket layer initialized

07/30/2008 11:55:30 PM	ubuntu	NetworkManager	<debug> [1217462130.925141] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 

07/30/2008 11:55:30 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Beginning DHCP transaction. 

07/30/2008 11:55:30 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 

07/30/2008 11:55:30 PM	ubuntu	NetworkManager	<info>  DHCP daemon state is now 12 (successfully started) for interface eth0 

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	add_service_record: got record id 0x10000

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	add_service_record: got record id 0x10001

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	add_service_record: got record id 0x10002

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	add_service_record: got record id 0x10003

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	audio.conf: Key file does not have group 'A2DP'

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	audio.conf: Key file does not have key 'Disable'

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	audio.conf: Key file does not have key 'Disable'

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	audio.conf: Key file does not have key 'Enable'

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	Bluetooth Audio daemon

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	Registered manager path:/org/bluez/audio

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	SEP 0x806d248 registered: type:0 codec:0 seid:1

07/30/2008 11:55:31 PM	ubuntu	audio[8435]	Unix socket created: 5

07/30/2008 11:55:31 PM	ubuntu	hcid[8414]	Created local server at unix:abstract=/var/run/dbus-VA2LwX5DCN,guid=4b920806e498481e7e74c8314890ff73

07/30/2008 11:55:31 PM	ubuntu	input[8446]	Bluetooth Input daemon

07/30/2008 11:55:31 PM	ubuntu	input[8446]	Registered input manager path:/org/bluez/input

07/30/2008 11:55:31 PM	ubuntu	kernel	[  317.298016] Bluetooth: L2CAP ver 2.9

07/30/2008 11:55:31 PM	ubuntu	kernel	[  317.298029] Bluetooth: L2CAP socket layer initialized

07/30/2008 11:55:31 PM	ubuntu	kernel	[  317.518910] Bluetooth: RFCOMM socket layer initialized

07/30/2008 11:55:31 PM	ubuntu	kernel	[  317.518943] Bluetooth: RFCOMM TTY layer initialized

07/30/2008 11:55:31 PM	ubuntu	kernel	[  317.518948] Bluetooth: RFCOMM ver 1.8

07/30/2008 11:55:31 PM	ubuntu	none	last message repeated 3 times

07/30/2008 11:55:32 PM	ubuntu	/usr/sbin/cron[8480]	(CRON) INFO (pidfile fd = 3)

07/30/2008 11:55:32 PM	ubuntu	/usr/sbin/cron[8481]	(CRON) INFO (Running @reboot jobs)

07/30/2008 11:55:32 PM	ubuntu	/usr/sbin/cron[8481]	(CRON) STARTUP (fork ok)

07/30/2008 11:55:33 PM	ubuntu	kernel	[  319.718116] NET: Registered protocol family 17

07/30/2008 11:55:33 PM	ubuntu	NetworkManager	<info>  DHCP daemon state is now 1 (starting) for interface eth0 

07/30/2008 11:55:34 PM	ubuntu	dhclient	DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

07/30/2008 11:55:34 PM	ubuntu	dhclient	DHCPOFFER of 192.168.0.226 from 192.168.0.1

07/30/2008 11:55:34 PM	ubuntu	dhclient	DHCPREQUEST of 192.168.0.226 on eth0 to 255.255.255.255 port 67

07/30/2008 11:55:35 PM	ubuntu	avahi-daemon[8003]	Interface eth0.IPv4 no longer relevant for mDNS.

07/30/2008 11:55:35 PM	ubuntu	avahi-daemon[8003]	Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.226.

07/30/2008 11:55:35 PM	ubuntu	avahi-daemon[8003]	Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.226.

07/30/2008 11:55:35 PM	ubuntu	avahi-daemon[8003]	Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.226.

07/30/2008 11:55:35 PM	ubuntu	avahi-daemon[8003]	New relevant interface eth0.IPv4 for mDNS.

07/30/2008 11:55:35 PM	ubuntu	avahi-daemon[8003]	New relevant interface eth0.IPv4 for mDNS.

07/30/2008 11:55:35 PM	ubuntu	avahi-daemon[8003]	Registering new address record for 192.168.0.226 on eth0.IPv4.

07/30/2008 11:55:35 PM	ubuntu	avahi-daemon[8003]	Registering new address record for 192.168.0.226 on eth0.IPv4.

07/30/2008 11:55:35 PM	ubuntu	avahi-daemon[8003]	Withdrawing address record for 192.168.0.226 on eth0.

07/30/2008 11:55:35 PM	ubuntu	dhcdbd	message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name

07/30/2008 11:55:35 PM	ubuntu	dhcdbd	message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

07/30/2008 11:55:35 PM	ubuntu	dhcdbd	message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain

07/30/2008 11:55:35 PM	ubuntu	dhcdbd	message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

07/30/2008 11:55:35 PM	ubuntu	dhclient	bound to 192.168.0.226 -- renewal in 227 seconds.

07/30/2008 11:55:35 PM	ubuntu	dhclient	DHCPACK of 192.168.0.226 from 192.168.0.1

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>    address 192.168.0.226 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>    broadcast 192.168.0.255 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>  DHCP daemon state is now 2 (bound) for interface eth0 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>    domain name 'mshome.net' 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>    gateway 192.168.0.1 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>    nameserver 192.168.0.1 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>    netmask 255.255.255.0 

07/30/2008 11:55:35 PM	ubuntu	NetworkManager	<info>  Retrieved the following IP4 configuration from the DHCP daemon: 

07/30/2008 11:55:36 PM	ubuntu	NetworkManager	<info>  Clearing nscd hosts cache. 

07/30/2008 11:55:36 PM	ubuntu	NetworkManager	<WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  

07/30/2008 11:55:37 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Finish handler scheduled. 

07/30/2008 11:55:37 PM	ubuntu	NetworkManager	<info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 

07/30/2008 11:55:37 PM	ubuntu	NetworkManager	<info>  Activation (eth0) successful, device activated. 

07/30/2008 11:55:38 PM	ubuntu	kernel	[  325.627925] NET: Registered protocol family 10

07/30/2008 11:55:38 PM	ubuntu	kernel	[  325.628855] lo: Disabled Privacy Extensions

07/30/2008 11:55:39 PM	ubuntu	ntpdate[8705]	step time server 91.189.94.4 offset -100796.287840 sec

---

### Post by kuja on 2008-07-29
I was only skimming but I didn't really see anything there; however, I didn't really expect to. You dont' get to see the really interesting messages until you do something that causes trouble. Of course the problem with that is you're going to have a really rought time (read as, you can't) as you by then you won't be able to access the logs. 

I'm still interested in seeing what it does if you force it to use the **"vesa"** driver, as I've never known it to have this sort of problem. It's a near flawless fallback for vesa complaint cards, albeit it has no hardware acceleration at all. There may be an option along the bottom (before you select the "start or install, check cd for defects, etc" options) - it will be on that screen) that lets you make it use vesa on the livecd, please try to give it a try.

---

### Post by abrasax on 2008-07-30
Tried. Works like a charm. Resolution is excellent, I can log out and restart. I'm installing kubuntu now. I'll let you now if it's ok. Thank you so much.

---

### Post by abrasax on 2008-07-30
OK. installed it. It works. Resolution is 1024x768. I need 1200x800 for my laptop. So now i need to install drivers for my graphics card. I'll try the second link you gave me. Hope it works.
For all other users that have the same problem with logging out of kubuntu/ubuntu it doesn't matter if you use splash or no. Just add boot command "xforcevesa" after ro quiet splash. It will work for sure.

---

### Post by abrasax on 2008-07-30
Could you please explain how to do this tutorial:
[http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)
in kubuntu. i get to the part where i should check the kernel version and replace if it doesn't match. I don't know what to do there so i just skip that bit then type sudo ./makedriver and i get this message:

root@divinity:~/K8M890XF40069-kernel-src_20060620/src# sudo ./makedriver
 -------- Check source code --------
cp: cannot create directory `/usr/src/xc/programs/Xserver/hw/xfree86/drivers/': No such file or directory
 -- via folder not found--------
 -- Please copy via folder into /usr/src/xc/programs/Xserver/hw/xfree86/drivers folder

And the site doesn't say anything about that.
Please help.:confused:

---

### Post by abrasax on 2008-08-07
I did it! But not on Kubuntu. I installed ubuntu 8.04 and followed the instructions from some german site:

[http:///amilo1703-vs-ubuntu.over-blog.org/]("http:///amilo1703-vs-ubuntu.over-blog.org/")

I can't speak a word of german but it's quite easy. If anyone has the same problem this will help. Thanks to all who tried to help me. I have a feeling i'll be back soon. :)

---

