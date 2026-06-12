---
title: "ndis wrapper problem"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by fireonyx on 2006-01-14
I have installed ubuntu just yesterday, and now I am trying to get my ndis wrapper to work.  I only have wireless for the moment, so I downloaded the latest ndis wrapper in windows, copied over to my home directory, and unzipped it.  I copied my .inf and .sys to my home directory as well.  I am having several problems..  It doesnt recognize the ndis wrapper as a module, as when I modprobe it, it cant find it.   Also, when I try to do the line to change Radio 1 to Radio 0, it gives me invalid permissions.  I made a script of all what I did, and as you will see, I know just enough of linux to get myself into trouble.  (Like, how do I end my script after I am done? :D)  Anyways, here is the script, and any help on ironing this out would be a great help!  As I am copying it from notepad in winblows, you will see some odd characters.

Script started on Sun 15 Jan 2006 01:41:58 AM EST
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo modprobe -r bcmwl5
Password:
FATAL: Module bcmwl5 not found.
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo apt-get remove ndiswrapper-utils

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree... Done

The following packages will be REMOVED:
  ndiswrapper-utils
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 131kB disk space will be freed.
Do you want to continue [Y/n]? y


(Reading database ... 73210 files and directories currently installed.)
Removing ndiswrapper-utils ...
dpkg - warning: while removing ndiswrapper-utils, directory `/etc/ndiswrapper' not empty so not removed.
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo rm -r /etc/ndiswrapper/
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo rm-  -r /etc/modprobe.d/ndiswrapper
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo su andrew
]0;andrew@ubuntu: ~andrew@ubuntu:~$ dpkg -i ndiswrapper*.deb
dpkg: requested operation requires superuser privilege
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo dpkg -i ndiswrapper*.deb
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 73198 files and directories currently installed.)
Unpacking ndiswrapper-utils (from ndiswrapper-utils_1.7-1_i386.deb) ...
Setting up ndiswrapper-utils (1.7-1) ...
]0;andrew@ubuntu: ~andrew@ubuntu:~$ ls
[00m[01;32mbcmwl5.inf[00m  [01;34mDesktop[00m   [01;32mndiswr~1.gz[00m      [01;31mndiswrapper-utils_1.7-1_i386.deb[00m
[01;32mbcmwl5.sys[00m  [01;32mndiswr~1[00m  [01;34mndiswrapper-1.7[00m  [00mwrapper[00m
[m]0;andrew@ubuntu: ~andrew@ubuntu:~$ ndiswrapper -i d bcmwl5.inf 
bash: ndiswrapper: command not found
]0;andrew@ubuntu: ~andrew@ubuntu:~$ ndiswrapper-1.7/      r
bash: ndiswrapper: command not found
]0;andrew@ubuntu: ~andrew@ubuntu:~$ ndiswrapper -i bcmwl5.inf 
andrew@ubuntu:~$ ls[Ksudo dpkg -i ndiswrapper*.deb
andrew@ubuntu:~$ ls[Kndiswrapper -i bcmwl5.inf 
andrew@ubuntu:~$ ls[Ksudo dpkg -i ndiswrapper*.deb
dpkg: status database area is locked by another process
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo dpkg -i ndiswrapper*.deb
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 73198 files and directories currently installed.)
Unpacking ndiswrapper-utils (from ndiswrapper-utils_1.7-1_i386.deb) ...
Setting up ndiswrapper-utils (1.7-1) ...
]0;andrew@ubuntu: ~andrew@ubuntu:~$ ndiswrapper
bash: ndiswrapper: command not found
]0;andrew@ubuntu: ~andrew@ubuntu:~$ /usr/sbin/ndiswrapper
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
]0;andrew@ubuntu: ~andrew@ubuntu:~$ /usr/sbin/ndiswrapper -i bcmwl5.inf 
Installing bcmwl5
Unable to create directory /etc/ndiswrapper/bcmwl5.Make sure you are running as root
]0;andrew@ubuntu: ~andrew@ubuntu:~$ /usr/sbin/ndiswrapper -i bcmwl5.inf [1@s[1@u[1@d[1@o[1@ 
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo /usr/sbin/ndiswrapper -l
Installed drivers:
bcmwl5		driver present, hardware present 
]0;andrew@ubuntu: ~andrew@ubuntu:~$ modprob       sudo modr probe ndiswrapper
FATAL: Module ndiswrapper not found.
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo /usr/sbin/ndiswrapper -m
modprobe config already contains alias directive

]0;andrew@ubuntu: ~andrew@ubuntu:~$ for conffile in /etc/ndiswrapper/bcmwl5// *.conf; do  
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:103C:12F3.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1355.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1356.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1357.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:103C:1358.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:103C:1359.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:103C:135A.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:0E11:00E7.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12F4.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12F8.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12FA.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12FB.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12F9.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12FC.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12FD.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
bash: syntax error near unexpected token `do'
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do do    
sudo: for: command not found
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
andrew@ubuntu:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $con
nffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile; done[A
andrew@ubuntu:~$ [34Psudo /usr/sbin/ndiswrapper -m

[K[Aandrew@ubuntu:~$ sudo /usr/sbin/ndiswrapper -m
andrew@ubuntu:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $con
nffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile; done[A
andrew@ubuntu:~$ [8Psudo for conffile in /etc/ndiswrapper/bcmwl5/*.conf; d

[K[Aandrew@ubuntu:~$ sudo for conffile in /etc/ndiswrapper/bcmwl5/*.conf; dodo [1P[1P[1P[1P[1P
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4301:103C:12F3.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4301.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1355.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1356.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:103C:1357.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:103C:1358.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:103C:1359.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:103C:135A.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:0E11:00E7.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12F4.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12F8.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12FA.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:103C:12FB.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12F9.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12FC.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:103C:12FD.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo m depmod -a
]0;andrew@ubuntu: ~andrew@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
]0;andrew@ubuntu: ~andrew@ubuntu:~$ dmesg
94667.296000] Allocating PCI resources starting at 30000000 (gap: 30000000:cec00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda5 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 1592.886 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.990000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.991000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.003000] Memory: 640132k/654272k available (1415k kernel code, 13444k reserved, 763k data, 224k init, 0k highmem)
[4294668.003000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.003000] Calibrating delay loop... 3137.53 BogoMIPS (lpj=1568768)
[4294668.023000] Security Framework v1.0.0 initialized
[4294668.023000] SELinux:  Disabled at boot.
[4294668.023000] Mount-cache hash table entries: 512
[4294668.023000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[4294668.023000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[4294668.023000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294668.023000] CPU: L2 Cache: 512K (64 bytes/line)
[4294668.023000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000010 00000001 00000000 00000001
[4294668.023000] CPU: AMD Turion(tm) 64 Mobile Technology ML-28 stepping 02
[4294668.023000] Enabling fast FPU save and restore... done.
[4294668.023000] Enabling unmasked SIMD FPU exception support... done.
[4294668.023000] Checking 'hlt' instruction... OK.
[4294668.027000] Checking for popad bug... OK.
[4294668.027000] checking if image is initramfs... it is
[4294668.483000] Freeing initrd memory: 4821k freed
[4294668.483000] ACPI: Looking for DSDT in initrd... not found!
[4294668.541000]  not found!
[4294668.552000] ENABLING IO-APIC IRQs
[4294668.552000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294668.674000] NET: Registered protocol family 16
[4294668.674000] EISA bus registered
[4294668.674000] ACPI: bus type pci registered
[4294668.674000] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=6
[4294668.674000] PCI: Using configuration type 1
[4294668.674000] mtrr: v2.0 (20020519)
[4294668.674000] ACPI: Subsystem revision 20050729
[4294668.680000] ACPI: Interpreter enabled
[4294668.680000] ACPI: Using IOAPIC for interrupt routing
[4294668.680000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.680000] PCI: Probing PCI hardware (bus 00)
[4294668.680000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.684000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[4294668.686000] Boot video device is 0000:01:05.0
[4294668.686000] PCI: Transparent bridge - 0000:00:14.4
[4294668.690000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.692000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[4294668.692000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[4294668.694000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[4294668.694000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[4294668.694000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[4294668.694000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[4294668.696000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[4294668.696000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[4294668.698000] burst-mode-ec-10-Aug
[4294668.698000] ACPI: Embedded Controller [EC0] (gpe 24)
[4294668.700000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[4294668.700000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294668.702000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.702000] pnp: PnP ACPI init
[4294668.706000] pnp: PnP ACPI: found 10 devices
[4294668.706000] PnPBIOS: Disabled by ACPI PNP
[4294668.706000] PCI: Using ACPI for IRQ routing
[4294668.706000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.750000] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[4294668.750000] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[4294668.750000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[4294668.750000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[4294668.750000] audit: initializing netlink socket (disabled)
[4294668.750000] audit: initialized
[4294668.750000] VFS: Disk quotas dquot_6.5.1
[4294668.750000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.750000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.750000] devfs: boot_options: 0x0
[4294668.752000] Initializing Cryptographic API
[4294668.752000] isapnp: Scanning for PnP cards...
[4294669.458000] isapnp: No Plug & Play device found
[4294669.494000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[4294669.508000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.510000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.510000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.514000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[4294669.514000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[4294669.514000] io scheduler noop registered
[4294669.514000] io scheduler anticipatory registered
[4294669.514000] io scheduler deadline registered
[4294669.514000] io scheduler cfq registered
[4294669.516000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.518000] EISA: Probing bus 0 at eisa.0
[4294669.518000] Cannot allocate resource for EISA slot 1
[4294669.518000] Cannot allocate resource for EISA slot 8
[4294669.518000] EISA: Detected 0 cards.
[4294669.518000] NET: Registered protocol family 2
[4294669.540000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294669.540000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[4294669.542000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.542000] TCP: Hash tables configured (established 131072 bind 65536)
[4294669.544000] NET: Registered protocol family 8
[4294669.544000] NET: Registered protocol family 20
[4294669.544000] ACPI wakeup devices: 
[4294669.544000] KBC0 MSE0  P2P AUDO 
[4294669.544000] ACPI: (supports S0 S3 S4 S5)
[4294669.544000] Freeing unused kernel memory: 224k freed
[4294669.574000] vga16fb: initializing
[4294669.574000] vga16fb: mapped to 0xc00a0000
[4294669.758000] Console: switching to colour frame buffer device 80x30
[4294669.758000] fb0: VGA16 VGA frame buffer device
[4294669.774000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.010000] Capability LSM initialized
[4294671.030000] NET: Registered protocol family 1
[4294671.052000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.052000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.052000] ACPI: bus type ide registered
[4294671.070000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[4294671.070000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[4294671.070000] ATIIXP: chipset revision 0
[4294671.070000] ATIIXP: not 100% native mode: will probe irqs later
[4294671.070000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[4294671.070000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[4294671.070000] Probing IDE interface ide0...
[4294671.348000] hda: IC25N060ATMR04-0, ATA DISK drive
[4294671.972000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.972000] Probing IDE interface ide1...
[4294672.666000] hdc: PIONEER DVDRW DVR-K15, ATAPI CD/DVD-ROM drive
[4294673.290000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.290000] Probing IDE interface ide2...
[4294673.816000] Probing IDE interface ide3...
[4294674.340000] Probing IDE interface ide4...
[4294674.864000] Probing IDE interface ide5...
[4294675.394000] hda: max request size: 1024KiB
[4294675.432000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[4294675.434000] hda: cache flushes supported
[4294675.434000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 p6 > p4
[4294675.574000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
[4294675.574000] Uniform CD-ROM driver Revision: 3.20
[4294676.082000] Attempting manual resume
[4294676.138000] swsusp: Suspend partition has wrong signature?
[4294676.218000] usbcore: registered new driver usbfs
[4294676.218000] usbcore: registered new driver hub
[4294676.220000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294676.220000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294676.220000] ohci_hcd 0000:00:13.0: PCI device 1002:4374 (ATI Technologies Inc)
[4294676.550000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[4294676.550000] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[4294676.610000] hub 1-0:1.0: USB hub found
[4294676.610000] hub 1-0:1.0: 4 ports detected
[4294676.616000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[4294676.616000] ohci_hcd 0000:00:13.1: PCI device 1002:4375 (ATI Technologies Inc)
[4294676.945000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[4294676.945000] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[4294677.005000] hub 2-0:1.0: USB hub found
[4294677.005000] hub 2-0:1.0: 4 ports detected
[4294677.041000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[4294677.041000] ehci_hcd 0000:00:13.2: PCI device 1002:4373 (ATI Technologies Inc)
[4294677.041000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[4294677.041000] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[4294677.041000] ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294677.041000] hub 3-0:1.0: USB hub found
[4294677.041000] hub 3-0:1.0: 8 ports detected
[4294677.233000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294677.233000] 8139cp: pci dev 0000:05:00.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[4294677.233000] 8139cp: Try the "8139too" driver instead.
[4294677.237000] 8139too Fast Ethernet driver 0.9.27
[4294677.237000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294677.239000] eth0: RealTek RTL8139 at 0xa000, 00:c0:9f:c1:8d:dd, IRQ 18
[4294677.239000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[4294677.471000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[4294679.341000] usbcore: registered new driver hiddev
[4294679.357000] input: USB HID v1.10 Mouse [Darfon USB Optical Mouse] on usb-0000:00:13.0-2
[4294679.357000] usbcore: registered new driver usbhid
[4294679.357000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294680.059000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294680.059000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294680.063000] ACPI: Thermal Zone [THRM] (53 C)
[4294680.739000] Attempting manual resume
[4294680.763000] swsusp: Suspend partition has wrong signature?
[4294680.861000] kjournald starting.  Commit interval 5 seconds
[4294680.861000] EXT3-fs: mounted filesystem with ordered data mode.
[4294683.693000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294689.805000] Adding 425680k swap on /dev/hda6.  Priority:-1 extents:1
[4294690.409000] EXT3 FS on hda5, internal journal
[4294708.631000] lp: driver loaded but no devices found
[4294708.681000] mice: PS/2 mouse device common for all mice
[4294708.749000] ieee1394: Initialized config rom entry `ip1394'
[4294708.777000] SCSI subsystem initialized
[4294708.785000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294710.415000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[4294710.421000] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[4294710.933000] ts: Compaq touchscreen protocol output
[4294716.875000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294718.895000] cdrom: open failed.
[4294720.317000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294720.419000] NTFS volume version 3.1.
[4294724.155000] Linux agpgart interface v0.101 (c) Dave Jones
[4294724.655000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294724.677000] shpchp: shpc_init : shpc_cap_offset == 0
[4294724.677000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294725.575000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[4294727.765000] Linux Kernel Card Services
[4294727.765000]   options:  [pci] [cardbus] [pm]
[4294727.789000] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294727.789000] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[4294727.789000] Yenta: Enabling burst memory read transactions
[4294727.789000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294727.789000] Yenta: Routing CardBus interrupts to PCI
[4294727.789000] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x64
[4294728.011000] Yenta: ISA IRQ mask 0x0ee8, PCI irq 17
[4294728.011000] Socket status: 30000006
[4294728.227000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294728.227000] ACPI: PCI Interrupt 0000:05:09.2[C] -> GSI 22 (level, low) -> IRQ 22
[4294728.337000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c0208800-c0208fff]  Max Packet=[2048]
[4294729.601000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f000066ffd4]
[4294731.575000] Real Time Clock Driver v1.12
[4294731.747000] input: PC Speaker
[4294736.865000] ACPI: AC Adapter [ACAD] (on-line)
[4294737.031000] ACPI: Battery Slot [BAT1] (battery present)
[4294737.071000] ACPI: Power Button (FF) [PWRF]
[4294737.071000] ACPI: Power Button (CM) [PWRB]
[4294737.071000] ACPI: Sleep Button (CM) [SLPB]
[4294737.071000] ACPI: Lid Switch [LID]
[4294737.281000] ibm_acpi: ec object not found
[4294737.407000] wmi_add device=dff52000
[4294737.407000] calling WQBA
[4294737.503000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294759.317000] apm: BIOS not found.
[4294761.215000] cs: IO port probe 0x100-0x4ff: clean.
[4294761.223000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[4294761.225000] cs: IO port probe 0xa00-0xaff: clean.
[4294761.657000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[4294761.657000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4 (1450 mV)
[4294761.657000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[4294761.657000] cpu_init done, current fid 0x8, vid 0x4
[4294761.859000] Bluetooth: Core ver 2.7
[4294761.859000] NET: Registered protocol family 31
[4294761.859000] Bluetooth: HCI device and connection manager initialized
[4294761.859000] Bluetooth: HCI socket layer initialized
[4294761.887000] Bluetooth: L2CAP ver 2.7
[4294761.887000] Bluetooth: L2CAP socket layer initialized
[4294761.921000] Bluetooth: RFCOMM ver 1.5
[4294761.921000] Bluetooth: RFCOMM socket layer initialized
[4294761.921000] Bluetooth: RFCOMM TTY layer initialized
[4294772.855000] NET: Registered protocol family 10
[4294772.855000] Disabled Privacy Extensions on device c02eb280(lo)
[4294772.855000] IPv6 over IPv4 tunneling driver
[4295065.311000] ibm_acpi: ec object not found
[4295096.043000] APIC error on CPU0: 00(40)

---

### Post by Zelut on 2006-01-14
Well trying to make sense of some of those unrecognized characters it looks like you're not running with appropriate permissions. Lets use sudo in the below example:

sudo ndiswrapper -i bcmwl5.inf (this should prompt for your password, enter it).
sudo modprobe ndiswrapper
sudo ndiswrapper -m

What errors do these return?

---

### Post by fireonyx on 2006-01-14
andrew@ubuntu:~$ sudo ndiswrapper -i bcmwl5.inf
Password:
bcmwl5 is already installed. Use -e to remove it
andrew@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
andrew@ubuntu:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

andrew@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
andrew@ubuntu:~$

---

### Post by Zelut on 2006-01-14
well it looks like the driver is installed and its already expecting to load it automagically... 

do you not have any wireless?  are you using gnome?  ...

---

### Post by fireonyx on 2006-01-14
I am using gnome...  And yes, I have wireless on windows, not in ubuntu.  Since it gives me FATAL: Module ndiswrapper not found, I figured that would mean it cant find the module, nor does it have it loaded already...?

---

### Post by Zelut on 2006-01-14
This might be a longshot but lets try this...

System > Admin > Networking & see if it lists a wireless card.  If so you'll need to 'activate' it and you're in business.  While you're trying that I'm going to look thru your previous output & see if there is anything else I can think of.

---

### Post by fireonyx on 2006-01-14
When I go to System/Admin/Networking, there are 2 devices avaliable, eth0 and ppp0, which I believe are the ethernet (wired) card, and the dial-up modem.  In the dmesg command, there wasnt any ndiswrapper listed, which I thought it had to do before it was considered installed correctly.

---

### Post by Zelut on 2006-01-14
Ok, another thing I notice above is the RadioState doesn't look like its been updated.  Can you try that command again as root (not sudo)?

su
[password]

---

### Post by Zelut on 2006-01-14
...this seems weird but it doesn't look like ndiswrapper is properly installed.  Did you say you were using the latest copy you found?  I would try again with the ubuntu provided package (has always worked for me).

sudo apt-get remove ndiswrapper-utils
sudo apt-get install ndiswrapper-utils

(unfortunately all of the output above looks like a mess so its not really clear what steps to take, re-try, etc..)

---

### Post by fireonyx on 2006-01-14
when I tried su, I get authentication failed... so logged into root in recovery mode, typed out the commands, and didnt get any response, other then a new line..  not sure if that means it works or not...  will try that.

---

### Post by fireonyx on 2006-01-14
ok, did that, here is the results...


andrew@ubuntu:~$ sudo apt-get remove ndiswrapper-utils
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ndiswrapper-utils
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 73207 files and directories currently installed.)
Removing ndiswrapper-utils ...
andrew@ubuntu:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.7kB of archives.
After unpacking 131kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 73198 files and directories currently installed.)
Unpacking ndiswrapper-utils (from .../ndiswrapper-utils_1.1-4ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils (1.1-4ubuntu2) ...

andrew@ubuntu:~$ ndiswrapper
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
andrew@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
andrew@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
andrew@ubuntu:~$

---

### Post by Zelut on 2006-01-14
Ok lets try something else here...

**sudo updatedb** (update your system index to search for files)
**locate ndiswrapper.ko**

if not found do
**sudo depmod -a**

afterwards check your System > Admin > Networking for a wireless network device..

---

### Post by fireonyx on 2006-01-14
still no luck... however, I am currently borrowing someones wireless pcmcia card, and it is working...  so I can atleast respond quicker.  Here is the results..
andrew@ubuntu:~$ sudo updatedb
Password:
locate ndiswrapper.ko
andrew@ubuntu:~$ locate ndiswrapper.ko
andrew@ubuntu:~$ sudo depmod -a
andrew@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
andrew@ubuntu:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

andrew@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
andrew@ubuntu:~$ sudo updatedb
andrew@ubuntu:~$ locate ndiswrapper.ko
andrew@ubuntu:~$

---

### Post by Zelut on 2006-01-14
...almost on to the third page with these posts :)

Ok, at this point I'm thinking that it is related to your original installtion of ndiswrapper.  Lets try to get it completely removed, reboot, and try this from scratch.

I notice, originally, you were using some of the instructions from the 'how to get broadcom wireless to work...'.  Can you return there & use his removal steps?  I honestly have not had this much trouble with wireless since the first time I tried almost a year ago.  Sorry I don't have better results for you.

After we get it removed as best we can we'll start over..

---

### Post by fireonyx on 2006-01-14
Im working on that now...  have one problem though, when I updated my repositories, following the link he has, it is all listed as hoary, and I am using breezy.  I did a search/replace hoary for breezy, as I got errors when I did updates.  I am still getting some errors... here they are :
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

Other then that, I have done the complete removal he lists..

---

### Post by trubblemaker on 2006-01-14
Here's a link to some instructions [to remove ndiswrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall")  I had the same issue and I'm pretty sure that removing it and starting from scratch is what fixed it.  Good luck.

---

### Post by fireonyx on 2006-01-14
Ok, I finially have it working...  I did a complete reinstall of ubuntu, and had several other issues that I had to work out, but I am now running on my own wireless card.  I have a few other questions, but I think I will go to IRC to ask them.  Thanks for all the help!

---

