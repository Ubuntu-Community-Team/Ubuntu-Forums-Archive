---
title: "Upgrade from Kubuntu 8.04 to 8.10 - Doesn't Work!"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by TiredBird on 2009-03-29
Kubuntu 8.04 with KDE3 was working. An internet upgrade of that to 8.10 breaks the X server.

Single user mode (cli) works. GUI does not.

All suggestions will be greatly appreciated.
:confused:

---

### Post by SuperSonic4 on 2009-04-01
A clean install will probably be better overall, especially if you have a separate /home

What happens if you try xfix from the recovery menu in grub?

---

### Post by TiredBird on 2009-04-01
> **SuperSonic4 said:**
> A clean install will probably be better overall, especially if you have a separate /home

I do have a separate /home but I have shied away from the clean install for two reasons. (1) Booting from CD-ROM is only occasionally successful on my computer. (2) I can't get any of the live CD's to give me a working X-system, even though I have tried most of the kernal parameters.

> **SuperSonic4 said:**
> What happens if you try xfix from the recovery menu in grub?

Not familiar with 'xfix'. Since my grub menu is of my own making, I assume you mean a command that can be given from the CLI that results from adding the 'single user' parameter to the kernal. In any event I don't think I have tried it.

On the other hand, I might have. When I boot with the single user kernal parameter it drops me into another menu which gives me a choice of attempting to fix the x-system. If that is xfix, then I have used it without success.

---

### Post by tonkabot on 2009-04-02
Okay, a bit more data than the first poster...

System is a Athlon 64 X2.
Graphics cards are nvidia 8800GT (a pair in SLI)

I upgraded my laptop, and that worked so well I went ahead and tried on my desktop.    There were 3 packages that failed to install (and still fail if I do the command line dist-upgrade (I forget if that is apt-get or dpkg), the first one being some etc?????.    Sorry working from aged memory here.

Anyway, now when I try to reboot X does not work.  if I type 'xstart' it says a few things, then '(EE) no devices found'.
There is some X program (nvidia-debug or something) that builds a great big log file, and the log file knows I have two nvidia 8800GT cards, but the nvidia-xconfig or nvidia-detector or something says no devices found.
(and it wants me to mail the log file somewhere, but no X no thunderbird, and the old 'cat logfile | mail bug@address' type of line doesn't work either.  Okay, apt-get and the internet work, so I could find the right package for command line mail and install it.)

I imagine the problem is the SLI (two cards) and may have to take one out for a bit, but does anyone have a clue what the fix is?

---

### Post by TiredBird on 2009-04-02
> **tonkabot said:**
> 
Okay, a bit more data than the first poster..


This thread was started because a more detailed posting had not found a fix. Having since learned a little more about proper posting procedures, I add the following:

I have a successful installation of 8.04 which I use daily. When I first installed it on my Toshiba laptop, M45-S165, it took considerable tweaking to get the video display and the wireless interface working, but both have been working fine now for some time.

I cloned the partition containing the working 8.04 and proceeded with a network upgrade.

There were no error messages or warnings during the install. However, after the system was installed and had rebooted, the video didn't work.

I got a 'two-ball' cursor which I was able to move around with my touchpad. However, the screen was blank, except for some reddish video noise in the top part of the screen.

I then looked at apt-get. In removing and reinstalling kubuntu-desktop, ubuntu-minimal and ubuntu-standard, I discovered a number of missing dependancies, but I wasn't able to fix them because my network didn't work either. 

I returned to the working 8.04 partition, (same machine as the failed install), and attempted to fix the dependencies in that. I was able to install all of the dependencies except 'desktop-effects-kde', 'jockey-common' and 'jockey-kde', as these broke the x-system when installed. I also could not install 'kubuntu-desktop' as that depended on the foregoing three packages.

The system still worked and I again cloned it to another partition and ran the install. I received no error messages or warnings but again the x-system was broken. 

I have compared the 'xorg.conf' files from both systems and found that the one from the 8.10 install contains nothing other than section headings. I have copied the working 'xorg.conf' from the 8.04 system to the failed 8.10 install, but that doesn't work either.

I have looked at all of the logs, but most particularly the x-system logs, and find no errors. I do however find some warnings, [ WW ], but don't find anything in those warnings that should result in a broken X.

Obviously I have done something wrong but for the life of me I can't figure out what it is. It would be greatly appreciated if someone would point me in the right direction.

Although I am not by any means a Linux guru, I do consider myself computer literate and have been using Linux for over five years. (I started with Red Hat 8 or 9.)

I have several computers, the newest being about 3 years old. All are running one or more versions of (K)ubuntu. My favorite, and the one I am trying to get working with 8.10, is a 1.5 GHz Toshiba Laptop with 1.5 GB of ram. 

Yes, I prefer the gui, but I also use the command line for a lot of what I do. 

And yes, I always install from deb packages. (Although I do not want to test or modify someone else's code, I do use C, C++, PHP and bash scripting for my own personal use.)

If there is anything more you need to know in order to help, please do not hesitate to ask.

---

### Post by TiredBird on 2009-04-02
I have again cloned my working 8.04 on this machine and attempted to upgrade it to 8.10. 

On my first attempt, I did not have enough space for the upgrade. I increased the size of the partition, (using gparted live 0.3.3-0), and restarted. 

This time the update proceeded to completion. 

There were several questions asked regarding the replacement of configuration files. On a previous upgrade attempt I had decided to keep some of them - this time I chose to replace all of them.

The upgrade went to conclusion without losing the connection.

When the system shut down and rebooted, I watched the messages carefully. All startup scripts posted a completion of [ OK ]. (I have yet to figure out how to stop these messages or look at them later. Although they blast by pretty fast, I didn't see any with [fail].)

When the boot process finally completed I has faced with the same unusable screen I had had on previous upgrade attempts. 

There was some reddish gibberish at the top of the screen, (about two lines worth), then about six lines of gray gibberish, and a movable cursor similar to my usual boot up cursor, (probably a gray scale representation of an artist's palette,) but larger than I usually get. 

Ctrl-alt-F1 through ctrl-alt-F6 did nothing. The system was apparently hung.

I turned the power off in order to regain control. 

I have not made any changes in the upgrade partition. In order to preserve the exact state resulting from the upgrade, I am cloning the partition and will use the clone for any needed investigations.

It is now a week since I began trying to upgrade. I have expended over 50 hours in trying to make this work. I have searched the internet and this forum for directions on how to solve this problem and cannot find one. 

Since so many people have 8.10 working 'as advertised', I am sure it is something that I am doing wrong.

Please, would someone help me with this.

---

### Post by norwoods on 2009-04-02
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.44 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig
if you can only run cli, you will have to use apt-get to install and run sudo nvidia-xconfig to create a new xorg.conf file.

---

### Post by TiredBird on 2009-04-02
> **norwoods said:**
> ...nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT...

I don't think this applies to me. I am running a 32 bit laptop with an on-board ATI Radeon graphics chip set. It looks like it might help tonkabot though.

Anyway, thanks for your post.

---

### Post by TiredBird on 2009-04-02
I have successfully installed 8.10 on another machine that is linked by LAN to the laptop that will not take the install.

Still looking for help getting the gui on my laptop to work.

Any suggestions will be greatly appreciated.

---

### Post by TiredBird on 2009-04-02
I have completed copying the partition containing the failed install of 8.10. The copy was made of the partition as it existed at the first sign of failure. It should now be possible to retrieve any logs or other files that might provide clues for fixing the gui.

I still need help. I hope someone can offer some suggestions.

Thanks in advance.

---

### Post by TiredBird on 2009-04-02
Following are both of the xorg.conf files: (The original comment lines  have been removed. The comments added by the update process remain.)

1) xorg.conf from the working 8.04 partition -

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:5:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Integral"
	VendorName	"Toshiba"
	ModelName	"15.4 in TFT active matrix 1280 x 800 WXGA TruBrite"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Integral"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth	24
		Modes 	"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

2) xorg.conf as modified by the upgrade to 8.10

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Emulate3Buttons"	"true"
#EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:5:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Integral"
	VendorName	"Toshiba"
	ModelName	"15.4 in TFT active matrix 1280 x 800 WXGA TruBrite"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Integral"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth	24
		Modes 	"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
# commented out by update-manager, HAL is now used
#	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

Perhaps someone familiar with the X directives can tell me what needs to be done.

---

### Post by TiredBird on 2009-04-02
Following is the last content from /var/log/messages. (The date and time stamp at the beginning of each line has been removed to reduce amount of text.)

```
syslogd 1.5.0#2ubuntu6: restart.
kernel: Inspecting /boot/System.map-2.6.25-2-386
kernel: Loaded 26961 symbols from /boot/System.map-2.6.25-2-386.
kernel: Symbols match kernel version 2.6.25.
kernel: Loaded 13763 symbols from 78 modules.
kernel: [    0.000000] Linux version 2.6.25-2-386 (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu8) ) #1 Tue Sep 30 14:47:35 UTC 2008
kernel: [    0.000000] BIOS-provided physical RAM map:
kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000005beb0000 (usable)
kernel: [    0.000000]  BIOS-e820: 000000005beb0000 - 000000005beb8000 (ACPI data)
kernel: [    0.000000]  BIOS-e820: 000000005beb8000 - 000000005bf00000 (ACPI NVS)
kernel: [    0.000000]  BIOS-e820: 000000005bf00000 - 000000005c000000 (reserved)
kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
kernel: [    0.000000] 574MB HIGHMEM available.
kernel: [    0.000000] 896MB LOWMEM available.
kernel: [    0.000000] Scan SMP from c0000000 for 1024 bytes.
kernel: [    0.000000] Scan SMP from c009fc00 for 1024 bytes.
kernel: [    0.000000] Scan SMP from c00f0000 for 65536 bytes.
kernel: [    0.000000] found SMP MP-table at [c00f7890] 000f7890
kernel: [    0.000000] Zone PFN ranges:
kernel: [    0.000000]   DMA             0 ->     4096
kernel: [    0.000000]   Normal       4096 ->   229376
kernel: [    0.000000]   HighMem    229376 ->   376496
kernel: [    0.000000] Movable zone start PFN for each node
kernel: [    0.000000] early_node_map[1] active PFN ranges
kernel: [    0.000000]     0:        0 ->   376496
kernel: [    0.000000] DMI present.
kernel: [    0.000000] ACPI: RSDP 000F7840, 0014 (r0 TOSINV)
kernel: [    0.000000] ACPI: RSDT 5BEB42B0, 0038 (r1 TOSINV   RSDT    6040000  LTP        0)
kernel: [    0.000000] ACPI: FACP 5BEB7EF6, 0074 (r1 TOSINV Goldfish  6040000 ATI     F4240)
kernel: [    0.000000] ACPI: DSDT 5BEB4704, 37F2 (r1 TOSINV    SB400  6040000 MSFT  100000E)
kernel: [    0.000000] ACPI: FACS 5BEB8FC0, 0040
kernel: [    0.000000] ACPI: APIC 5BEB7F6A, 005A (r1 TOSINV ^I APIC    6040000  LTP        0)
kernel: [    0.000000] ACPI: MCFG 5BEB7FC4, 003C (r1 TOSINV   MCFG    6040000  LTP        0)
kernel: [    0.000000] ACPI: SSDT 5BEB44E3, 0221 (r1 TOSINV  Cpu0Cst     3001 INTL 20030224)
kernel: [    0.000000] ACPI: SSDT 5BEB42E8, 01FB (r1 TOSINV    CpuPm     3000 INTL 20030224)
kernel: [    0.000000] ACPI: DMI detected: Toshiba
kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
kernel: [    0.000000] Processor #0 6:13 APIC version 20
kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
kernel: [    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
kernel: [    0.000000] Using ACPI for processor (LAPIC) configuration information
kernel: [    0.000000] Intel MultiProcessor Specification v1.4
kernel: [    0.000000]     Virtual Wire compatibility mode.
kernel: [    0.000000] OEM ID:   Product ID: RS400 Board APIC at: 0xFEE00000
kernel: [    0.000000] I/O APIC #1 Version 33 at 0xFEC00000.
kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
kernel: [    0.000000] Processors: 1
kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 5c000000:84000000)
kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 373555
kernel: [    0.000000] Kernel command line: root=LABEL=8100kde4 ro noapic
kernel: [    0.000000] Enabling fast FPU save and restore... done.
kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
kernel: [    0.000000] Initializing CPU#0
kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
kernel: [    0.000000] Detected 1496.413 MHz processor.
kernel: [    0.004000] Console: colour VGA+ 80x25
kernel: [    0.004000] console [tty0] enabled
kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
kernel: [    0.004000] Memory: 1479312k/1505984k available (2161k kernel code, 25372k reserved, 963k data, 356k init, 588480k highmem)
kernel: [    0.004000] virtual kernel memory layout:
kernel: [    0.004000]     fixmap  : 0xfffa6000 - 0xfffff000   ( 356 kB)
kernel: [    0.004000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
kernel: [    0.004000]       .init : 0xc0410000 - 0xc0469000   ( 356 kB)
kernel: [    0.004000]       .data : 0xc031c676 - 0xc040d620   ( 963 kB)
kernel: [    0.004000]       .text : 0xc0100000 - 0xc031c676   (2161 kB)
kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
kernel: [    0.084008] Calibrating delay using timer specific routine.. 2996.05 BogoMIPS (lpj=5992115)
kernel: [    0.084162] Security Framework initialized
kernel: [    0.084229] SELinux:  Disabled at boot.
kernel: [    0.084285] Capability LSM initialized
kernel: [    0.084341] Mount-cache hash table entries: 512
kernel: [    0.084644] Initializing cgroup subsys ns
kernel: [    0.084711] Initializing cgroup subsys cpuacct
kernel: [    0.084780] CPU: L1 I cache: 32K, L1 D cache: 32K
kernel: [    0.084870] CPU: L2 cache: 1024K
kernel: [    0.084933] Compat vDSO mapped to ffffe000.
kernel: [    0.084988] CPU: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
kernel: [    0.085125] Checking 'hlt' instruction... OK.
kernel: [    0.102264] Freeing SMP alternatives: 0k freed
kernel: [    0.102318] ACPI: Core revision 20070126
kernel: [    0.111393] ACPI: setting ELCR to 0200 (from 0800)
kernel: [    0.116007] net_namespace: 540 bytes
kernel: [    0.116007] Booting paravirtualized kernel on bare hardware
kernel: [    0.116007] NET: Registered protocol family 16
kernel: [    0.116007] EISA bus registered
kernel: [    0.116007] ACPI: bus type pci registered
kernel: [    0.116007] PCI: Using MMCONFIG for extended config space
kernel: [    0.116007] PCI: Using configuration type 1
kernel: [    0.116007] Setting up standard PCI resources
kernel: [    0.124100] ACPI: Interpreter enabled
kernel: [    0.124153] ACPI: (supports S0 S3 S4 S5)
kernel: [    0.124374] ACPI: Using PIC for interrupt routing
kernel: [    0.164011] ACPI: EC: GPE = 0x7, I/O: command/status = 0x66, data = 0x62
kernel: [    0.164011] ACPI: EC: driver started in poll mode
kernel: [    0.164011] ACPI: PCI Root Bridge [PCI0] (0000:00)
kernel: [    0.164347] PCI: Transparent bridge - 0000:00:14.4
kernel: [    0.167004] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
kernel: [    0.167339] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
kernel: [    0.167671] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
kernel: [    0.168002] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
kernel: [    0.168299] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0
kernel: [    0.168669] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
kernel: [    0.169078] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
kernel: [    0.169489] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
kernel: [    0.169890] ACPI: Power Resource [PFA1] (off)
kernel: [    0.170147] Linux Plug and Play Support v0.97 (c) Adam Belay
kernel: [    0.170236] pnp: PnP ACPI init
kernel: [    0.170292] ACPI: bus type pnp registered
kernel: [    0.188013] pnp: PnP ACPI: found 10 devices
kernel: [    0.188013] ACPI: ACPI bus type pnp unregistered
kernel: [    0.188013] PnPBIOS: Disabled by ACPI PNP
kernel: [    0.188013] PCI: Using ACPI for IRQ routing
kernel: [    0.188013] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
kernel: [    0.188013] NET: Registered protocol family 8
kernel: [    0.188013] NET: Registered protocol family 20
kernel: [    0.188013] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
kernel: [    0.188013] system 00:08: ioport range 0x1080-0x1080 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0x220-0x22f has been reserved
kernel: [    0.188013] system 00:08: ioport range 0x400-0x401 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0x40b-0x40b has been reserved
kernel: [    0.188013] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0x530-0x537 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0xc00-0xc01 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0xc14-0xc14 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0xc50-0xc52 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0xc6c-0xc6c has been reserved
kernel: [    0.188013] system 00:08: ioport range 0xc6f-0xc6f has been reserved
kernel: [    0.188013] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0xcd8-0xcdf has been reserved
kernel: [    0.188013] system 00:08: ioport range 0x8000-0x805f has been reserved
kernel: [    0.188013] system 00:08: ioport range 0xf40-0xf47 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0x280-0x293 has been reserved
kernel: [    0.188013] system 00:08: ioport range 0x87f-0x87f has been reserved
kernel: [    0.188013] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
kernel: [    0.188013] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
kernel: [    0.188013] system 00:09: iomem range 0x0-0xfff could not be reserved
kernel: [    0.218498] PCI: Bridge: 0000:00:01.0
kernel: [    0.218550]   IO window: 9000-9fff
kernel: [    0.218601]   MEM window: 0xc0100000-0xc01fffff
kernel: [    0.218653]   PREFETCH window: 0x00000000d0000000-0x00000000dfffffff
kernel: [    0.218710] PCI: Bus 3, cardbus bridge: 0000:02:06.0
kernel: [    0.218761]   IO window: 0x0000a000-0x0000a0ff
kernel: [    0.218815]   IO window: 0x0000a400-0x0000a4ff
kernel: [    0.218870]   PREFETCH window: 0x60000000-0x63ffffff
kernel: [    0.218925]   MEM window: 0x64000000-0x67ffffff
kernel: [    0.218979] PCI: Bridge: 0000:00:14.4
kernel: [    0.219030]   IO window: a000-bfff
kernel: [    0.219085]   MEM window: 0xc0200000-0xc03fffff
kernel: [    0.219139]   PREFETCH window: 0x0000000060000000-0x0000000063ffffff
kernel: [    0.219420] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
kernel: [    0.219479] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
kernel: [    0.219635] NET: Registered protocol family 2
kernel: [    0.219771] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
kernel: [    0.220219] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
kernel: [    0.222730] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
kernel: [    0.223600] TCP: Hash tables configured (established 131072 bind 65536)
kernel: [    0.223660] TCP reno registered
kernel: [    0.224101] checking if image is initramfs... it is
kernel: [    1.213183] Freeing initrd memory: 8855k freed
kernel: [    1.214709] audit: initializing netlink socket (disabled)
kernel: [    1.214791] type=2000 audit(1238681598.208:1): initialized
kernel: [    1.215092] highmem bounce pool size: 64 pages
kernel: [    1.217411] VFS: Disk quotas dquot_6.5.1
kernel: [    1.217507] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
kernel: [    1.217768] io scheduler noop registered
kernel: [    1.217819] io scheduler anticipatory registered
kernel: [    1.217870] io scheduler deadline registered
kernel: [    1.217932] io scheduler cfq registered (default)
kernel: [    1.244094] ACPI: EC: non-query interrupt received, switching to interrupt mode
kernel: [    1.268612] isapnp: Scanning for PnP cards...
kernel: [    1.623617] isapnp: No Plug & Play device found
kernel: [    1.649934] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
kernel: [    1.650971] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
kernel: [    1.651028] ACPI: PCI Interrupt 0000:00:14.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
kernel: [    1.651180] ACPI: PCI interrupt for device 0000:00:14.6 disabled
kernel: [    1.652008] brd: module loaded
kernel: [    1.652161] input: Macintosh mouse button emulation as /class/input/input0
kernel: [    1.652327] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
kernel: [    1.654788] serio: i8042 KBD port at 0x60,0x64 irq 1
kernel: [    1.654844] serio: i8042 AUX port at 0x60,0x64 irq 12
kernel: [    1.655098] mice: PS/2 mouse device common for all mice
kernel: [    1.655280] EISA: Probing bus 0 at eisa.0
kernel: [    1.655339] Cannot allocate resource for EISA slot 1
kernel: [    1.655420] Cannot allocate resource for EISA slot 8
kernel: [    1.655471] EISA: Detected 0 cards.
kernel: [    1.655522] cpuidle: using governor ladder
kernel: [    1.656153] NET: Registered protocol family 1
kernel: [    1.656234] Using IPI Shortcut mode
kernel: [    1.656423] registered taskstats version 1
kernel: [    1.656594] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
kernel: [    1.657250] Freeing unused kernel memory: 356k freed
kernel: [    1.692973] input: AT Translated Set 2 keyboard as /class/input/input1
kernel: [    1.807090] fuse init (API version 7.9)
kernel: [    1.813039] ACPI: Transitioning device [FAN1] to D3
kernel: [    1.813176] ACPI: PNP0C0B:00 is registered as cooling_device0
kernel: [    1.813232] ACPI: Fan [FAN1] (off)
kernel: [    1.819791] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
kernel: [    1.820057] ACPI: ACPI0007:00 is registered as cooling_device1
kernel: [    1.820095] ACPI: Processor [CPU0] (supports 8 throttling states)
kernel: [    1.836070] Marking TSC unstable due to: TSC halts in idle.
kernel: [    1.932280] ACPI: LNXTHERM:01 is registered as thermal_zone0
kernel: [    1.964052] ACPI: Thermal Zone [TZCR] (67 C)
kernel: [    1.983547] device-mapper: uevent: version 1.0.3
kernel: [    1.983711] device-mapper: ioctl: 4.13.0-ioctl (2007-10-18) initialised: [email]dm-devel@redhat.com[/email]
kernel: [    2.004333] md: linear personality registered for level -1
kernel: [    2.009992] md: multipath personality registered for level -4
kernel: [    2.015251] md: raid0 personality registered for level 0
kernel: [    2.021533] md: raid1 personality registered for level 1
kernel: [    2.026752] xor: automatically using best checksumming function: pIII_sse
kernel: [    2.043961]    pIII_sse  :  3905.000 MB/sec
kernel: [    2.044011] xor: using function: pIII_sse (3905.000 MB/sec)
kernel: [    2.044801] async_tx: api initialized (async)
kernel: [    2.095968] Clocksource tsc unstable (delta = -104809823 ns)
kernel: [    2.116042] raid6: int32x1    529 MB/s
kernel: [    2.184063] raid6: int32x2    594 MB/s
kernel: [    2.252059] raid6: int32x4    538 MB/s
kernel: [    2.320036] raid6: int32x8    405 MB/s
kernel: [    2.387996] raid6: mmxx1     1554 MB/s
kernel: [    2.456017] raid6: mmxx2     1768 MB/s
kernel: [    2.523997] raid6: sse1x1    1103 MB/s
kernel: [    2.592027] raid6: sse1x2    1821 MB/s
kernel: [    2.660032] raid6: sse2x1    1983 MB/s
kernel: [    2.728015] raid6: sse2x2    2244 MB/s
kernel: [    2.728064] raid6: using algorithm sse2x2 (2244 MB/s)
kernel: [    2.728116] md: raid6 personality registered for level 6
kernel: [    2.728167] md: raid5 personality registered for level 5
kernel: [    2.728217] md: raid4 personality registered for level 4
kernel: [    2.762269] md: raid10 personality registered for level 10
kernel: [    3.740237] usbcore: registered new interface driver usbfs
kernel: [    3.740328] usbcore: registered new interface driver hub
kernel: [    3.744789] usbcore: registered new device driver usb
kernel: [    3.746155] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
kernel: [    3.746326] ohci_hcd 0000:00:13.0: OHCI Host Controller
kernel: [    3.748869] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
kernel: [    3.748958] ohci_hcd 0000:00:13.0: irq 11, io mem 0xc0000000
kernel: [    3.788179] Uniform Multi-Platform E-IDE driver
kernel: [    3.788245] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
kernel: [    3.804319] usb usb1: configuration #1 chosen from 1 choice
kernel: [    3.804410] hub 1-0:1.0: USB hub found
kernel: [    3.804476] hub 1-0:1.0: 4 ports detected
kernel: [    3.908288] ACPI: PCI Interrupt 0000:00:13.2[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
kernel: [    3.908468] ehci_hcd 0000:00:13.2: EHCI Host Controller
kernel: [    3.908547] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
kernel: [    3.908667] ehci_hcd 0000:00:13.2: irq 11, io mem 0xc0002000
kernel: [    3.920087] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
kernel: [    3.920262] usb usb2: configuration #1 chosen from 1 choice
kernel: [    3.920339] hub 2-0:1.0: USB hub found
kernel: [    3.920398] hub 2-0:1.0: 8 ports detected
kernel: [    4.024179] ATIIXP: IDE controller (0x1002:0x4376 rev 0x00) at  PCI slot 0000:00:14.1
kernel: [    4.024507] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
kernel: [    4.024560] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
kernel: [    4.024709] ATIIXP: not 100% native mode: will probe irqs later
kernel: [    4.024778]     ide0: BM-DMA at 0x8430-0x8437, BIOS settings: hda:DMA, hdb:PIO
kernel: [    4.024887]     ide1: BM-DMA at 0x8438-0x843f, BIOS settings: hdc:DMA, hdd:PIO
kernel: [    4.312585] hda: HTS541080G9AT00, ATA DISK drive
kernel: [    4.984438] hda: UDMA/100 mode selected
kernel: [    5.720672] hdc: MATSHITADVD-RAM UJ-840S, ATAPI CD/DVD-ROM drive
kernel: [    6.056585] hdc: UDMA/33 mode selected
kernel: [    6.057004] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
kernel: [    6.073244] ide1 at 0x170-0x177,0x376 on irq 15
kernel: [    6.076078] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
kernel: [    6.076321] ohci_hcd 0000:00:13.1: OHCI Host Controller
kernel: [    6.076399] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
kernel: [    6.076472] ohci_hcd 0000:00:13.1: irq 11, io mem 0xc0001000
kernel: [    6.132389] usb usb3: configuration #1 chosen from 1 choice
kernel: [    6.132469] hub 3-0:1.0: USB hub found
kernel: [    6.132532] hub 3-0:1.0: 4 ports detected
kernel: [    6.239866] No dock devices found.
kernel: [    6.250273] SCSI subsystem initialized
kernel: [    6.307181] hda: max request size: 512KiB
kernel: [    6.313052] hda: 156301488 sectors (80026 MB) w/7539KiB Cache, CHS=16383/255/63
kernel: [    6.313667] hda: cache flushes supported
kernel: [    6.313785]  hda: hda1 hda2 hda4 < hda5 hda6 hda7 hda8 hda9 hda10 hda11 hda12 hda13 >
kernel: [    6.471125] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
kernel: [    6.471447] Uniform CD-ROM driver Revision: 3.20
kernel: [    7.126232] kjournald starting.  Commit interval 5 seconds
kernel: [    7.126302] EXT3-fs: mounted filesystem with ordered data mode.
kernel: [   17.080324] udevd version 124 started
kernel: [   19.029339] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
kernel: [   19.051702] Linux agpgart interface v0.103
kernel: [   19.091260] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
kernel: [   19.378763] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
kernel: [   19.480070] input: Power Button (FF) as /class/input/input2
kernel: [   19.509055] ACPI: Power Button (FF) [PWRF]
kernel: [   19.509241] input: Power Button (CM) as /class/input/input3
kernel: [   19.537354] ACPI: Power Button (CM) [PWRB]
kernel: [   19.537520] input: Lid Switch as /class/input/input4
kernel: [   19.549386] ACPI: Lid Switch [LID]
kernel: [   19.566823] ACPI: AC Adapter [ADP0] (on-line)
kernel: [   19.921518] ACPI: Battery Slot [BAT0] (battery present)
kernel: [   21.353668] input: PC Speaker as /class/input/input5
kernel: [   21.433498] Yenta: CardBus bridge found at 0000:02:06.0 [1179:ff10]
kernel: [   21.434205] Yenta: Enabling burst memory read transactions
kernel: [   21.434261] Yenta: Using CSCINT to route CSC interrupts to PCI
kernel: [   21.434312] Yenta: Routing CardBus interrupts to PCI
kernel: [   21.434368] Yenta TI: socket 0000:02:06.0, mfunc 0x01111122, devctl 0x64
kernel: [   21.666043] Yenta: ISA IRQ mask 0x04f8, PCI irq 11
kernel: [   21.666106] Socket status: 30000068
kernel: [   21.666159] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
kernel: [   21.666212] cs: IO port probe 0xa000-0xbfff: clean.
kernel: [   21.666863] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc03fffff
kernel: [   21.666916] pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x63ffffff
kernel: [   22.030051] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
kernel: [   22.030124] synaptics: Toshiba Satellite M45 detected, limiting rate to 40pps.
kernel: [   22.063259] input: SynPS/2 Synaptics TouchPad as /class/input/input6
kernel: [   22.313413] pccard: CardBus card inserted into slot 0
kernel: [   22.364899] cs: IO port probe 0x100-0x3af: clean.
kernel: [   22.367508] cs: IO port probe 0x3e0-0x4ff: clean.
kernel: [   22.368617] cs: IO port probe 0x820-0x8ff: clean.
kernel: [   22.369587] cs: IO port probe 0xc00-0xcf7: clean.
kernel: [   22.370527] cs: IO port probe 0xa00-0xaff: clean.
kernel: [   22.434410] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
kernel: [   22.434531] PCI: Enabling device 0000:03:00.0 (0000 -> 0003)
kernel: [   22.434594] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
kernel: [   22.436645] tulip0:  MII transceiver #1 config 3100 status 7849 advertising 05e1.
kernel: [   22.456376] eth0: ADMtek Comet rev 17 at Port 0xa000, 00:09:5b:8b:41:0d, IRQ 11.
kernel: [   22.611603] lp: driver loaded but no devices found
kernel: [   22.940484] Adding 1052184k swap on /dev/hda5.  Priority:-1 extents:1 across:1052184k
kernel: [   23.369156] EXT3 FS on hda2, internal journal
kernel: [   25.494076] kjournald starting.  Commit interval 5 seconds
kernel: [   25.494354] EXT3 FS on hda11, internal journal
kernel: [   25.494360] EXT3-fs: mounted filesystem with ordered data mode.
kernel: [   25.745128] kjournald starting.  Commit interval 5 seconds
kernel: [   25.745468] EXT3 FS on hda6, internal journal
kernel: [   25.745473] EXT3-fs: mounted filesystem with ordered data mode.
kernel: [   25.781554] kjournald starting.  Commit interval 5 seconds
kernel: [   25.781918] EXT3 FS on hda7, internal journal
kernel: [   25.781922] EXT3-fs: mounted filesystem with ordered data mode.
kernel: [   25.819131] kjournald starting.  Commit interval 5 seconds
kernel: [   25.827038] EXT3 FS on hda8, internal journal
kernel: [   25.827042] EXT3-fs: mounted filesystem with ordered data mode.
kernel: [   26.466114] ip_tables: (C) 2000-2006 Netfilter Core Team
kernel: [   28.005878] NET: Registered protocol family 17
kernel: [   30.121575] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
kernel: [   30.404852] NET: Registered protocol family 10
kernel: [   30.406046] lo: Disabled Privacy Extensions
kernel: [   33.102629] apm: BIOS not found.
kernel: [   33.270225] ppdev: user-space parallel port driver dhcdbd: Started up.
kernel: [   36.451444] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
kernel: [   36.675512] [drm] Initialized drm 1.1.0 20060810
kernel: [   36.737635] [drm] Initialized radeon 1.28.0 20060524 on minor 0
kernel: [   37.391148] [drm] Setting GART location based on new memory map
kernel: [   37.392853] [drm] Loading R300 Microcode
kernel: [   37.392911] [drm] writeback test succeeded in 1 usecs
kernel: [   42.269688] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
```

---

### Post by TiredBird on 2009-04-02
Following is the last content from /var/log/kdm.log

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux toshiba-laptop 2.6.25-2-386 #1 Tue Sep 30 14:47:35 UTC 2008 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr  2 09:13:53 2009
(==) Using config file: "/etc/X11/xorg.conf"
NTSC PAL NTSC-J 
finished output detect: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
in RADEONProbeOutputModes
after xf86InitialConfiguration
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
init memmap
init common
init crtc1
init pll1
restore memmap
restore common
restore crtc1
restore pll1
restore LVDS

```

---

### Post by TiredBird on 2009-04-03
Following is the last content from /var/log/Xorg.0.log

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux toshiba-laptop 2.6.25-2-386 #1 Tue Sep 30 14:47:35 UTC 2008 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr  2 09:13:53 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Integral"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:5:0) ATI Technologies Inc RS400 [Radeon Xpress 200M] rev 0, Mem @ 0xd0000000/0, 0xc0100000/0, I/O @ 0x00009000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "v4l"

(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "ati"

(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) v4l driver for Video4Linux
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610, ATI RV670,
	ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE, ATI Radeon HD 3470,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI FireMV 2450, ATI FireMV 2260,
	ATI FireMV 2260, ATI ATI Radeon HD 3600 Series,
	ATI ATI Radeon HD 3650 AGP, ATI ATI Radeon HD 3600 PRO,
	ATI ATI Radeon HD 3600 XT, ATI ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for v4l
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000c0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5A42 (PCIE)" (ChipID = 0x5a42)
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): PCI card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(II) RADEON(0): Direct rendering experimental on RS400/Xpress 200 enabled
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 1432, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 100, max_in_pll: 1350, xclk: 16600, sclk: 166.000000, mclk: 300.000000
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=40000; xclk=16600
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x68, DACType-2, TMDSType-2, ConnectorType-1
(II) RADEON(0): Port4: DDCType-0x1a0, DACType-0, TMDSType-0, ConnectorType-7
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Integral
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: LPL                     
(II) RADEON(0): Panel Size from BIOS: 1280x800
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 71250
HBlank: 160, HOverPlus: 48, HSyncWidth: 32
VBlank: 23, VOverPlus: 2, VSyncWidth: 6
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL NTSC-J 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x68
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- 0x1a0
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) RADEON(0): Year: 2004  Week: 0
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  330 x 210 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0):  LGPhilipsLCD
(II) RADEON(0):  LP154W01-A5K2
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00320c000000000000
(II) RADEON(0): 	000e0102802115780a0f109758528828
(II) RADEON(0): 	23505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26002115100000190000000000000000
(II) RADEON(0): 	00000000000000000000000000fe004c
(II) RADEON(0): 	475068696c6970734c43440a000000fe
(II) RADEON(0): 	004c503135345730312d41354b320029
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) RADEON(0): Year: 2004  Week: 0
(II) RADEON(0): EDID Version: 1.2
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  330 x 210 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block 0
(II) RADEON(0):  LGPhilipsLCD
(II) RADEON(0):  LP154W01-A5K2
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00320c000000000000
(II) RADEON(0): 	000e0102802115780a0f109758528828
(II) RADEON(0): 	23505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26002115100000190000000000000000
(II) RADEON(0): 	00000000000000000000000000fe004c
(II) RADEON(0): 	475068696c6970734c43440a000000fe
(II) RADEON(0): 	004c503135345730312d41354b320029
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "LPL", prod id 0
(II) RADEON(0):     EDID quirk: Detailed timings give sizes in cm.
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using user preference for initial modes
(II) RADEON(0): Output LVDS using initial mode 800x600
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit d0000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(II) RADEON(0): Dynamic Clock Scaling Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Using 32 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 29 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1280,1202)
(II) RADEON(0): Largest offscreen area available: 1280 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1248000
(II) RADEON(0): Will use depth buffer at offset 0x1824000
(II) RADEON(0): Will use 34816 kb for textures at offset 0x1e00000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xd0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 32768 kB allocated with handle 0xf8c17000
(II) RADEON(0): [pci] ring handle = 0xf8c17000
(II) RADEON(0): [pci] Ring mapped at 0xb78ad000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf8d18000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb78ac000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf8d19000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xb35e5000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf8f19000
(II) RADEON(0): [pci] GART Texture map mapped at 0xb1965000
(II) RADEON(0): [drm] register handle = 0xc0100000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5c00 0x5fff5c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 11
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x5fff5c00 is: 0x5fff5c00
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0x61ff6000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5c00 0x5fff5c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0x61ff6000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): XAA Render acceleration unsupported on Radeon 9500/9700 and newer. Please use EXA instead.
(II) RADEON(0): Render acceleration disabled
(WW) RADEON(0): Failed to determine num pipes from DRM, falling back to manual look-up!
(II) RADEON(0): num quad-pipes is 4
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x005de800
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x005e3800
(II) RADEON(0): Largest offscreen area available: 1280 x 6981
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"

(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x5fff5c00 0x5fff5c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0x61ff6000
restore common
restore crtc1
restore pll1
restore LVDS
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "MergedFB" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 330 x 210
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event6"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc104"
(**) AT Translated Set 2 keyboard: xkb_model: "pc104"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

```

---

### Post by TiredBird on 2009-04-09
The solution was to switch from Kubuntu 8.10 to Ubuntu 8.10. The later worked for me 'out of the box'.

I am tagging this thread as 'solved'.

---

