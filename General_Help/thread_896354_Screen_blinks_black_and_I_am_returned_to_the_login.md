---
title: "Screen blinks black and I am returned to the login screen"
date: 2008-08-21
forum: General Help
---

### Post by Ingo88 on 2008-08-21
I am experiencing a rather weird and very annoying problem in Ubuntu (Hardy). I did experience this in Gutsy too, but not as often as in Hardy.

Sometimes, at completely random occasions (while burning a cd with K3b, while reading my webmail in firefox etc.) the screen goes black for a second, returns to normal for a second, and then suddenly I am brought back to the login screen. This sure could be enraging especially if I'd have some unsaved documents or e-mail messages open when it happens. Luckily I haven't been that unfortunate yet.

When I upgraded to Hardy I first tried to install Kubuntu as I mostly use KDE apps (K3b, digiKam, Gwenview), but there I was kicked back to the login screen about all the time. Besides, it was way slower than Ubuntu.

Any clues what the problem might be? I intend to use Hardy throughout the LTS period, but I sure can't live with problems like this.

Thanks in advance for your help!

Here's the lshw for the computer:

```
    description: Computer
    product: VT82C694X
    vendor: Fujitsu Siemens
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal
  *-core
       description: Motherboard
       product: MS-6323
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (06/30/00)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.3
          slot: SLOT 1
          size: 733MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-cache:0
          description: L1 cache
          physical id: 8
          slot: Internal Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back
     *-cache:1
          description: L2 cache
          physical id: 9
          slot: External Cache
          size: 256KiB
          capacity: 2MiB
          capabilities: synchronous external write-back
     *-memory
          description: Flash Memory
          physical id: 17
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 256MiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: BANK_1
             size: 256MiB
     *-pci:0
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c4
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via module=via_agp
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage 128 PF/PRO AGP 4x TMDS
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=32 mingnt=8
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: Maxtor 32049H3
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: BAC5
                serial: N30J679C
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f57df57d
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: ebc88406-1be8-4eb1-899d-788a5cfc5a92
                   size: 4510MiB
                   capacity: 4510MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-08-06 09:32:17 filesystem=ext3 modified=2008-08-20 20:33:06 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-08-20 15:01:04 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 13GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 980MiB
                      capabilities: nofs
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM SR-8585
                vendor: MATSHITA
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1S29
                serial: [MATSHITADVD-ROM SR-8585 1S29PM  02/10/00
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-R/RW MP7200A
                vendor: RICOH
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.20
                serial: [RICOH   CD-R/RW MP7200A 1.200
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1


             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax/Voice Modem
             vendor: Rockwell International
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 10
             bus info: pci@0000:00:10.0
             logical name: eth0
             version: 10
             serial: 00:10:a7:0e:fd:06
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.151 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: Host bridge
          product: VT82C686 [Apollo Super ACPI]
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:07.4
          version: 30
          width: 32 bits
          clock: 33MHz
```

---

### Post by Ingo88 on 2008-09-12
Anyone?

This is a serious problem. Please don't make me give up on Ubuntu :(

---

### Post by ajmorris on 2008-09-12
hi there,
can you please post your /var/log/syslog file.
and you /var/log/Xorg.0.log

AJ

---

### Post by chalewa on 2008-09-12
this happens to me sometimes, but usually if i just login a couple more times, it will be fine

---

### Post by Ingo88 on 2008-09-20
Thanks for your replies!

Here are the logs you asked for:

syslog:
```
Sep 20 11:56:38 helena syslogd 1.5.0#1ubuntu1: restart.
Sep 20 11:56:38 helena anacron[5649]: Job `cron.daily' terminated (mailing output)
Sep 20 11:56:38 helena anacron[5649]: Normal exit (1 job run)
Sep 20 11:56:39 helena postfix/pickup[5274]: 10D4B432CE: uid=0 from=<root>
Sep 20 11:56:39 helena postfix/cleanup[6515]: 10D4B432CE: message-id=<20080920085639.10D4B432CE@helena>
Sep 20 11:56:39 helena postfix/qmgr[5275]: 10D4B432CE: from=<root@helena>, size=422, nrcpt=1 (queue active)
Sep 20 11:56:39 helena postfix/local[6517]: 10D4B432CE: to=<helena@helena>, orig_to=<root>, relay=local, delay=0.28, delays=0.21/0.02/0/0.06, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Sep 20 11:56:39 helena postfix/qmgr[5275]: 10D4B432CE: removed
Sep 20 12:17:01 helena /USR/SBIN/CRON[6523]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 20 12:38:36 helena -- MARK --
Sep 20 12:58:36 helena -- MARK --
Sep 20 13:17:01 helena /USR/SBIN/CRON[6542]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 20 13:38:36 helena -- MARK --
Sep 20 13:58:36 helena -- MARK --
Sep 20 14:17:01 helena /USR/SBIN/CRON[6609]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 20 14:24:09 helena init: tty4 main process (4800) killed by TERM signal
Sep 20 14:24:09 helena init: tty5 main process (4801) killed by TERM signal
Sep 20 14:24:09 helena init: tty2 main process (4805) killed by TERM signal
Sep 20 14:24:09 helena init: tty3 main process (4806) killed by TERM signal
Sep 20 14:24:09 helena init: tty6 main process (4809) killed by TERM signal
Sep 20 14:24:09 helena init: tty1 main process (5812) killed by TERM signal
Sep 20 14:24:13 helena avahi-daemon[5118]: Got SIGTERM, quitting.
Sep 20 14:24:13 helena avahi-daemon[5118]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.151.
Sep 20 14:24:13 helena postfix/master[5267]: terminating on signal 15
Sep 20 14:24:15 helena kernel: [11213.235023] ip6_tables: (C) 2000-2006 Netfilter Core Team
Sep 20 14:24:17 helena exiting on signal 15
Sep 20 14:26:47 helena syslogd 1.5.0#1ubuntu1: restart.
Sep 20 14:26:48 helena kernel: Inspecting /boot/System.map-2.6.24-19-generic
Sep 20 14:26:48 helena kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Sep 20 14:26:48 helena kernel: Symbols match kernel version 2.6.24.
Sep 20 14:26:48 helena kernel: Loaded 15236 symbols from 72 modules.
Sep 20 14:26:48 helena kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 20 14:26:48 helena kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 20 14:26:48 helena kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Sep 20 14:26:48 helena kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 20 14:26:48 helena kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Sep 20 14:26:48 helena kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 20 14:26:48 helena kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Sep 20 14:26:48 helena kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Sep 20 14:26:48 helena kernel: [    0.000000] 0MB HIGHMEM available.
Sep 20 14:26:48 helena kernel: [    0.000000] 512MB LOWMEM available.
Sep 20 14:26:48 helena kernel: [    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
Sep 20 14:26:48 helena kernel: [    0.000000] Zone PFN ranges:
Sep 20 14:26:48 helena kernel: [    0.000000]   DMA             0 ->     4096
Sep 20 14:26:48 helena kernel: [    0.000000]   Normal       4096 ->   131072
Sep 20 14:26:48 helena kernel: [    0.000000]   HighMem    131072 ->   131072
Sep 20 14:26:48 helena kernel: [    0.000000] Movable zone start PFN for each node
Sep 20 14:26:48 helena kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep 20 14:26:48 helena kernel: [    0.000000]     0:        0 ->   131072
Sep 20 14:26:48 helena kernel: [    0.000000] On node 0 totalpages: 131072
Sep 20 14:26:48 helena kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep 20 14:26:48 helena kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 20 14:26:48 helena kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep 20 14:26:48 helena kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Sep 20 14:26:48 helena kernel: [    0.000000]   Normal zone: 125984 pages, LIFO batch:31
Sep 20 14:26:48 helena kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Sep 20 14:26:48 helena kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Sep 20 14:26:48 helena kernel: [    0.000000] DMI 2.2 present.
Sep 20 14:26:48 helena kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
Sep 20 14:26:48 helena kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Sep 20 14:26:48 helena kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Sep 20 14:26:48 helena kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130048
Sep 20 14:26:48 helena kernel: [    0.000000] Kernel command line: root=UUID=ebc88406-1be8-4eb1-899d-788a5cfc5a92 ro splash acpi=off apm=power_off
Sep 20 14:26:48 helena kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Sep 20 14:26:48 helena kernel: [    0.000000] mapped APIC to ffffb000 (0140d000)
Sep 20 14:26:48 helena kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 20 14:26:48 helena kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 20 14:26:48 helena kernel: [    0.000000] Initializing CPU#0
Sep 20 14:26:48 helena kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Sep 20 14:26:48 helena kernel: [    0.000000] Detected 733.374 MHz processor.
Sep 20 14:26:48 helena kernel: [   19.571365] Console: colour VGA+ 80x25
Sep 20 14:26:48 helena kernel: [   19.571379] console [tty0] enabled
Sep 20 14:26:48 helena kernel: [   19.573604] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 20 14:26:48 helena kernel: [   19.574761] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 20 14:26:48 helena kernel: [   19.627512] Memory: 507400k/524288k available (2177k kernel code, 16376k reserved, 1006k data, 368k init, 0k highmem)
Sep 20 14:26:48 helena kernel: [   19.627617] virtual kernel memory layout:
Sep 20 14:26:48 helena kernel: [   19.627620]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep 20 14:26:48 helena kernel: [   19.627624]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 20 14:26:48 helena kernel: [   19.627628]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Sep 20 14:26:48 helena kernel: [   19.627632]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Sep 20 14:26:48 helena kernel: [   19.627636]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Sep 20 14:26:48 helena kernel: [   19.627639]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Sep 20 14:26:48 helena kernel: [   19.627643]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Sep 20 14:26:48 helena kernel: [   19.628114] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep 20 14:26:48 helena kernel: [   19.628313] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Sep 20 14:26:48 helena kernel: [   19.708414] Calibrating delay using timer specific routine.. 1468.89 BogoMIPS (lpj=2937789)
Sep 20 14:26:48 helena kernel: [   19.708591] Security Framework initialized
Sep 20 14:26:48 helena kernel: [   19.708668] SELinux:  Disabled at boot.
Sep 20 14:26:48 helena kernel: [   19.708759] AppArmor: AppArmor initialized
Sep 20 14:26:48 helena kernel: [   19.708826] Failure registering capabilities with primary security module.
Sep 20 14:26:48 helena kernel: [   19.708908] Mount-cache hash table entries: 512
Sep 20 14:26:48 helena kernel: [   19.709246] Initializing cgroup subsys ns
Sep 20 14:26:48 helena kernel: [   19.709314] Initializing cgroup subsys cpuacct
Sep 20 14:26:48 helena kernel: [   19.709394] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
Sep 20 14:26:48 helena kernel: [   19.709423] CPU: L1 I cache: 16K, L1 D cache: 16K
Sep 20 14:26:48 helena kernel: [   19.709526] CPU: L2 cache: 256K
Sep 20 14:26:48 helena kernel: [   19.709589] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
Sep 20 14:26:48 helena kernel: [   19.709613] Compat vDSO mapped to ffffe000.
Sep 20 14:26:48 helena kernel: [   19.709701] Checking 'hlt' instruction... OK.
Sep 20 14:26:48 helena kernel: [   19.725100] SMP alternatives: switching to UP code
Sep 20 14:26:48 helena kernel: [   19.728677] Freeing SMP alternatives: 11k freed
Sep 20 14:26:48 helena kernel: [   19.729087] Early unpacking initramfs... done
Sep 20 14:26:48 helena kernel: [   20.698678] CPU0: Intel Pentium III (Coppermine) stepping 03
Sep 20 14:26:48 helena kernel: [   20.698879] SMP motherboard not detected.
Sep 20 14:26:48 helena kernel: [   20.698941] Local APIC not detected. Using dummy APIC emulation.
Sep 20 14:26:48 helena kernel: [   20.699149] Brought up 1 CPUs
Sep 20 14:26:48 helena kernel: [   20.699259] CPU0 attaching sched-domain:
Sep 20 14:26:48 helena kernel: [   20.699267]  domain 0: span 01
Sep 20 14:26:48 helena kernel: [   20.699272]   groups: 01
Sep 20 14:26:48 helena kernel: [   20.699847] net_namespace: 64 bytes
Sep 20 14:26:48 helena kernel: [   20.699931] Booting paravirtualized kernel on bare hardware
Sep 20 14:26:48 helena kernel: [   20.701620] Time: 11:25:47  Date: 09/20/08
Sep 20 14:26:48 helena kernel: [   20.701766] NET: Registered protocol family 16
Sep 20 14:26:48 helena kernel: [   20.702452] EISA bus registered
Sep 20 14:26:48 helena kernel: [   20.735241] PCI: PCI BIOS revision 2.10 entry at 0xfb1f0, last bus=1
Sep 20 14:26:48 helena kernel: [   20.735315] PCI: Using configuration type 1
Sep 20 14:26:48 helena kernel: [   20.735405] Setting up standard PCI resources
Sep 20 14:26:48 helena kernel: [   20.738458] ACPI: Interpreter disabled.
Sep 20 14:26:48 helena kernel: [   20.738533] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep 20 14:26:48 helena kernel: [   20.738686] pnp: PnP ACPI: disabled
Sep 20 14:26:48 helena kernel: [   20.738754] PnPBIOS: Scanning system for PnP BIOS support...
Sep 20 14:26:48 helena kernel: [   20.739183] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbc20
Sep 20 14:26:48 helena kernel: [   20.739256] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbc50, dseg 0xf0000
Sep 20 14:26:48 helena kernel: [   20.742074] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
Sep 20 14:26:48 helena kernel: [   20.742853] PCI: Probing PCI hardware
Sep 20 14:26:48 helena kernel: [   20.742922] PCI: Probing PCI hardware (bus 00)
Sep 20 14:26:48 helena kernel: [   20.743372] PCI quirk: region 4000-40ff claimed by vt82c586 ACPI
Sep 20 14:26:48 helena kernel: [   20.743443] PCI quirk: region 5000-500f claimed by vt82c686 SMB
Sep 20 14:26:48 helena kernel: [   20.808229] NET: Registered protocol family 8
Sep 20 14:26:48 helena kernel: [   20.808304] NET: Registered protocol family 20
Sep 20 14:26:48 helena kernel: [   20.808570] AppArmor: AppArmor Filesystem Enabled
Sep 20 14:26:48 helena kernel: [   20.808759] system 00:07: iomem range 0x0-0x9ffff could not be reserved
Sep 20 14:26:48 helena kernel: [   20.808830] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
Sep 20 14:26:48 helena kernel: [   20.808911] system 00:07: iomem range 0x100000-0x1fffffff could not be reserved
Sep 20 14:26:48 helena kernel: [   20.809006] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
Sep 20 14:26:48 helena kernel: [   20.809075] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
Sep 20 14:26:48 helena kernel: [   20.809143] system 00:08: iomem range 0xf8000-0xfbfff could not be reserved
Sep 20 14:26:48 helena kernel: [   20.809214] system 00:08: iomem range 0xfc000-0xfffff could not be reserved
Sep 20 14:26:48 helena kernel: [   20.810468] PCI: Bridge: 0000:00:01.0
Sep 20 14:26:48 helena kernel: [   20.810535]   IO window: 9000-9fff
Sep 20 14:26:48 helena kernel: [   20.810599]   MEM window: e0000000-e1ffffff
Sep 20 14:26:48 helena kernel: [   20.810662]   PREFETCH window: dc000000-dfffffff
Sep 20 14:26:48 helena kernel: [   20.810743] PCI: Setting latency timer of device 0000:00:01.0 to 64
Sep 20 14:26:48 helena kernel: [   20.810778] NET: Registered protocol family 2
Sep 20 14:26:48 helena kernel: [   20.812206] Time: tsc clocksource has been installed.
Sep 20 14:26:48 helena kernel: [   20.844426] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Sep 20 14:26:48 helena kernel: [   20.845230] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Sep 20 14:26:48 helena kernel: [   20.848071] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 20 14:26:48 helena kernel: [   20.851335] TCP: Hash tables configured (established 65536 bind 65536)
Sep 20 14:26:48 helena kernel: [   20.851426] TCP reno registered
Sep 20 14:26:48 helena kernel: [   20.860674] checking if image is initramfs... it is
Sep 20 14:26:48 helena kernel: [   22.693557] Freeing initrd memory: 7735k freed
Sep 20 14:26:48 helena kernel: [   22.695132] audit: initializing netlink socket (disabled)
Sep 20 14:26:48 helena kernel: [   22.695245] audit(1221909949.064:1): initialized
Sep 20 14:26:48 helena kernel: [   22.701544] VFS: Disk quotas dquot_6.5.1
Sep 20 14:26:48 helena kernel: [   22.701878] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 20 14:26:48 helena kernel: [   22.702571] io scheduler noop registered
Sep 20 14:26:48 helena kernel: [   22.702642] io scheduler anticipatory registered
Sep 20 14:26:48 helena kernel: [   22.702704] io scheduler deadline registered
Sep 20 14:26:48 helena kernel: [   22.702811] io scheduler cfq registered (default)
Sep 20 14:26:48 helena kernel: [   22.702903] PCI: VIA PCI bridge detected. Disabling DAC.
Sep 20 14:26:48 helena kernel: [   22.702969] PCI: Disabling Via external APIC routing
Sep 20 14:26:48 helena kernel: [   22.703073] Boot video device is 0000:01:00.0
Sep 20 14:26:48 helena kernel: [   22.703740] isapnp: Scanning for PnP cards...
Sep 20 14:26:48 helena kernel: [   23.058565] isapnp: No Plug & Play device found
Sep 20 14:26:48 helena kernel: [   23.157017] Real Time Clock Driver v1.12ac
Sep 20 14:26:48 helena kernel: [   23.157303] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep 20 14:26:48 helena kernel: [   23.157645] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 20 14:26:48 helena kernel: [   23.159655] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 20 14:26:48 helena kernel: [   23.162041] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep 20 14:26:48 helena kernel: [   23.162339] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep 20 14:26:48 helena kernel: [   23.162708] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
Sep 20 14:26:48 helena kernel: [   23.162776] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Sep 20 14:26:48 helena kernel: [   23.163130] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 20 14:26:48 helena kernel: [   23.168157] mice: PS/2 mouse device common for all mice
Sep 20 14:26:48 helena kernel: [   23.168562] EISA: Probing bus 0 at eisa.0
Sep 20 14:26:48 helena kernel: [   23.168657] Cannot allocate resource for EISA slot 4
Sep 20 14:26:48 helena kernel: [   23.168720] Cannot allocate resource for EISA slot 5
Sep 20 14:26:48 helena kernel: [   23.168801] EISA: Detected 0 cards.
Sep 20 14:26:48 helena kernel: [   23.168865] cpuidle: using governor ladder
Sep 20 14:26:48 helena kernel: [   23.168927] cpuidle: using governor menu
Sep 20 14:26:48 helena kernel: [   23.169438] NET: Registered protocol family 1
Sep 20 14:26:48 helena kernel: [   23.169584] Using IPI No-Shortcut mode
Sep 20 14:26:48 helena kernel: [   23.169721] registered taskstats version 1
Sep 20 14:26:48 helena kernel: [   23.169996]   Magic number: 8:62:429
Sep 20 14:26:48 helena kernel: [   23.170265] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 20 14:26:48 helena kernel: [   23.170330] EDD information not available.
Sep 20 14:26:48 helena kernel: [   23.171079] Freeing unused kernel memory: 368k freed
Sep 20 14:26:48 helena kernel: [   23.190984] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Sep 20 14:26:48 helena kernel: [   24.873991] fuse init (API version 7.9)
Sep 20 14:26:48 helena kernel: [   24.962531] thermal: Unknown symbol acpi_processor_set_thermal_limit
Sep 20 14:26:48 helena kernel: [   25.985536] SCSI subsystem initialized
Sep 20 14:26:48 helena kernel: [   26.051429] usbcore: registered new interface driver usbfs
Sep 20 14:26:48 helena kernel: [   26.051496] usbcore: registered new interface driver hub
Sep 20 14:26:48 helena kernel: [   26.112799] usbcore: registered new device driver usb
Sep 20 14:26:48 helena kernel: [   26.123294] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Sep 20 14:26:48 helena kernel: [   26.123401] 8139cp 0000:00:10.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Sep 20 14:26:48 helena kernel: [   26.123410] 8139cp 0000:00:10.0: Try the "8139too" driver instead.
Sep 20 14:26:48 helena kernel: [   26.150455] 8139too Fast Ethernet driver 0.9.28
Sep 20 14:26:48 helena kernel: [   26.184802] eth0: RealTek RTL8139 at 0xc000, 00:10:a7:0e:fd:06, IRQ 11
Sep 20 14:26:48 helena kernel: [   26.184817] eth0:  Identified 8139 chip type 'RTL-8139C'
Sep 20 14:26:48 helena kernel: [   26.255270] USB Universal Host Controller Interface driver v3.0
Sep 20 14:26:48 helena kernel: [   26.255489] uhci_hcd 0000:00:07.2: UHCI Host Controller
Sep 20 14:26:48 helena kernel: [   26.255982] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Sep 20 14:26:48 helena kernel: [   26.256027] uhci_hcd 0000:00:07.2: irq 5, io base 0x0000a400
Sep 20 14:26:48 helena kernel: [   26.256377] usb usb1: configuration #1 chosen from 1 choice
Sep 20 14:26:48 helena kernel: [   26.256450] hub 1-0:1.0: USB hub found
Sep 20 14:26:48 helena kernel: [   26.256468] hub 1-0:1.0: 2 ports detected
Sep 20 14:26:48 helena kernel: [   26.297248] libata version 3.00 loaded.
Sep 20 14:26:48 helena kernel: [   26.359464] uhci_hcd 0000:00:07.3: UHCI Host Controller
Sep 20 14:26:48 helena kernel: [   26.359533] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
Sep 20 14:26:48 helena kernel: [   26.359571] uhci_hcd 0000:00:07.3: irq 5, io base 0x0000a800
Sep 20 14:26:48 helena kernel: [   26.359893] usb usb2: configuration #1 chosen from 1 choice
Sep 20 14:26:48 helena kernel: [   26.359961] hub 2-0:1.0: USB hub found
Sep 20 14:26:48 helena kernel: [   26.359978] hub 2-0:1.0: 2 ports detected
Sep 20 14:26:48 helena kernel: [   26.456158] Floppy drive(s): fd0 is 1.44M
Sep 20 14:26:48 helena kernel: [   26.477878] FDC 0 is a post-1991 82077
Sep 20 14:26:48 helena kernel: [   26.524294] pata_via 0000:00:07.1: version 0.3.3
Sep 20 14:26:48 helena kernel: [   26.543148] scsi0 : pata_via
Sep 20 14:26:48 helena kernel: [   26.563139] scsi1 : pata_via
Sep 20 14:26:48 helena kernel: [   26.563284] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xa000 irq 14
Sep 20 14:26:48 helena kernel: [   26.563293] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xa008 irq 15
Sep 20 14:26:48 helena kernel: [   26.855169] usb 2-1: new low speed USB device using uhci_hcd and address 2
Sep 20 14:26:48 helena kernel: [   26.891654] ata1.00: ATA-6: Maxtor 32049H3, BAC51KJ0, max UDMA/100
Sep 20 14:26:48 helena kernel: [   26.891671] ata1.00: 40021632 sectors, multi 16: LBA 
Sep 20 14:26:48 helena kernel: [   26.891733] ata1.01: ATAPI: MATSHITADVD-ROM SR-8585, 1S29, max UDMA/33
Sep 20 14:26:48 helena kernel: [   26.907569] ata1.00: configured for UDMA/66
Sep 20 14:26:48 helena kernel: [   27.037691] usb 2-1: configuration #1 chosen from 1 choice
Sep 20 14:26:48 helena kernel: [   27.072533] ata1.01: configured for UDMA/33
Sep 20 14:26:48 helena kernel: [   27.227254] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Sep 20 14:26:48 helena kernel: [   27.227271] ata2: failed to recover some devices, retrying in 5 secs
Sep 20 14:26:48 helena kernel: [   27.279072] usb 2-2: new full speed USB device using uhci_hcd and address 3
Sep 20 14:26:48 helena kernel: [   27.433537] usb 2-2: configuration #1 chosen from 1 choice
Sep 20 14:26:48 helena kernel: [   27.435369] hub 2-2:1.0: USB hub found
Sep 20 14:26:48 helena kernel: [   27.437365] hub 2-2:1.0: 4 ports detected
Sep 20 14:26:48 helena kernel: [   28.185368] usbcore: registered new interface driver hiddev
Sep 20 14:26:48 helena kernel: [   28.237357] input: Microsoft Microsoft USB Wireless Mouse as /devices/pci0000:00/0000:00:07.3/usb2/2-1/2-1:1.0/input/input2
Sep 20 14:26:48 helena kernel: [   28.246913] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:07.3-1
Sep 20 14:26:48 helena kernel: [   28.246966] usbcore: registered new interface driver usbhid
Sep 20 14:26:48 helena kernel: [   28.246978] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Sep 20 14:26:48 helena kernel: [   32.386234] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Sep 20 14:26:48 helena kernel: [   32.386250] ata2: failed to recover some devices, retrying in 5 secs
Sep 20 14:26:48 helena kernel: [   37.545271] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Sep 20 14:26:48 helena kernel: [   37.545287] ata2: failed to recover some devices, retrying in 5 secs
Sep 20 14:26:48 helena kernel: [   42.869411] ata2.00: ATAPI: RICOH   CD-R/RW MP7200A, 1.20, max UDMA/33
Sep 20 14:26:48 helena kernel: [   43.040223] ata2.00: configured for UDMA/33
Sep 20 14:26:48 helena kernel: [   43.040555] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 32049H3   BAC5 PQ: 0 ANSI: 5
Sep 20 14:26:48 helena kernel: [   43.042494] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-ROM SR-8585  1S29 PQ: 0 ANSI: 5
Sep 20 14:26:48 helena kernel: [   43.044368] scsi 1:0:0:0: CD-ROM            RICOH    CD-R/RW MP7200A  1.20 PQ: 0 ANSI: 5
Sep 20 14:26:48 helena kernel: [   43.095828] Driver 'sd' needs updating - please use bus_type methods
Sep 20 14:26:48 helena kernel: [   43.100357] sd 0:0:0:0: [sda] 40021632 512-byte hardware sectors (20491 MB)
Sep 20 14:26:48 helena kernel: [   43.100406] sd 0:0:0:0: [sda] Write Protect is off
Sep 20 14:26:48 helena kernel: [   43.100415] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 20 14:26:48 helena kernel: [   43.100475] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 20 14:26:48 helena kernel: [   43.100625] sd 0:0:0:0: [sda] 40021632 512-byte hardware sectors (20491 MB)
Sep 20 14:26:48 helena kernel: [   43.100659] sd 0:0:0:0: [sda] Write Protect is off
Sep 20 14:26:48 helena kernel: [   43.100667] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 20 14:26:48 helena kernel: [   43.100723] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 20 14:26:48 helena kernel: [   43.100735]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
Sep 20 14:26:48 helena kernel: [   43.138858]  sda5 sda6 >
Sep 20 14:26:48 helena kernel: [   43.139454] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 20 14:26:48 helena kernel: [   43.160541] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
Sep 20 14:26:48 helena kernel: [   43.160558] Uniform CD-ROM driver Revision: 3.20
Sep 20 14:26:48 helena kernel: [   43.160699] sr 0:0:1:0: Attached scsi CD-ROM sr0
Sep 20 14:26:48 helena kernel: [   43.164316] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 20 14:26:48 helena kernel: [   43.164378] sr 0:0:1:0: Attached scsi generic sg1 type 5
Sep 20 14:26:48 helena kernel: [   43.164431] sr 1:0:0:0: Attached scsi generic sg2 type 5
Sep 20 14:26:48 helena kernel: [   43.165380] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Sep 20 14:26:48 helena kernel: [   43.165540] sr 1:0:0:0: Attached scsi CD-ROM sr1
Sep 20 14:26:48 helena kernel: [   44.393601] Attempting manual resume
Sep 20 14:26:48 helena kernel: [   44.393615] swsusp: Resume From Partition 8:6
Sep 20 14:26:48 helena kernel: [   44.393620] PM: Checking swsusp image.
Sep 20 14:26:48 helena kernel: [   44.407264] PM: Resume from disk failed.
Sep 20 14:26:48 helena kernel: [   44.503033] kjournald starting.  Commit interval 5 seconds
Sep 20 14:26:48 helena kernel: [   44.503069] EXT3-fs: mounted filesystem with ordered data mode.
Sep 20 14:26:48 helena kernel: [   63.140579] input: PC Speaker as /devices/platform/pcspkr/input/input3
Sep 20 14:26:48 helena kernel: [   65.166996] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 20 14:26:48 helena kernel: [   65.204007] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 20 14:26:48 helena kernel: [   65.285577] parport_pc: VIA 686A/8231 detected
Sep 20 14:26:48 helena kernel: [   65.285590] parport_pc: probing current configuration
Sep 20 14:26:48 helena kernel: [   65.285616] parport_pc: Current parallel port base: 0x378
Sep 20 14:26:48 helena kernel: [   65.285678] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Sep 20 14:26:48 helena kernel: [   65.348026] Linux agpgart interface v0.102
Sep 20 14:26:48 helena kernel: [   65.379918] parport_pc: VIA parallel port: io=0x378, irq=7
Sep 20 14:26:48 helena kernel: [   65.571822] agpgart: Detected VIA Apollo Pro 133 chipset
Sep 20 14:26:48 helena kernel: [   65.575537] agpgart: AGP aperture is 64M @ 0xd8000000
Sep 20 14:26:48 helena kernel: [   65.959248] via686a 0000:00:07.4: base address not set - upgrade BIOS or use force_addr=0xaddr
Sep 20 14:26:48 helena kernel: [   66.941957] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep 20 14:26:48 helena kernel: [   69.535678] NET: Registered protocol family 10
Sep 20 14:26:48 helena kernel: [   69.536337] lo: Disabled Privacy Extensions
Sep 20 14:26:48 helena kernel: [   69.643653] PCI: Setting latency timer of device 0000:00:07.5 to 64
Sep 20 14:26:48 helena kernel: [   73.051448] lp0: using parport0 (interrupt-driven).
Sep 20 14:26:48 helena kernel: [   73.093870] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Sep 20 14:26:48 helena kernel: [   73.279101] Adding 1003988k swap on /dev/sda6.  Priority:-1 extents:1 across:1003988k
Sep 20 14:26:48 helena kernel: [   74.940717] EXT3 FS on sda1, internal journal
Sep 20 14:26:48 helena kernel: [   75.231232] device-mapper: uevent: version 1.0.3
Sep 20 14:26:48 helena kernel: [   75.231322] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Sep 20 14:26:48 helena kernel: [   77.415503] kjournald starting.  Commit interval 5 seconds
Sep 20 14:26:48 helena kernel: [   77.415904] EXT3 FS on sda5, internal journal
Sep 20 14:26:48 helena kernel: [   77.415916] EXT3-fs: mounted filesystem with ordered data mode.
Sep 20 14:26:48 helena kernel: [   78.756131] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 20 14:26:48 helena kernel: [   79.980911] eth0: no IPv6 routers present
Sep 20 14:26:48 helena kernel: [   80.376179] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
Sep 20 14:26:48 helena kernel: [   80.376392] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
Sep 20 14:26:48 helena kernel: [   80.377180] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
Sep 20 14:26:48 helena kernel: [   80.377505] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
Sep 20 14:26:49 helena NetworkManager: <info>  starting... 
Sep 20 14:26:50 helena avahi-daemon[5136]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Sep 20 14:26:50 helena avahi-daemon[5136]: Successfully dropped root privileges.
Sep 20 14:26:50 helena avahi-daemon[5136]: avahi-daemon 0.6.22 starting up.
Sep 20 14:26:50 helena avahi-daemon[5136]: Successfully called chroot().
Sep 20 14:26:50 helena avahi-daemon[5136]: Successfully dropped remaining capabilities.
Sep 20 14:26:50 helena avahi-daemon[5136]: No service file found in /etc/avahi/services.
Sep 20 14:26:50 helena avahi-daemon[5136]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.151.
Sep 20 14:26:50 helena avahi-daemon[5136]: New relevant interface eth0.IPv4 for mDNS.
Sep 20 14:26:50 helena avahi-daemon[5136]: Network interface enumeration completed.
Sep 20 14:26:50 helena avahi-daemon[5136]: Registering new address record for fe80::210:a7ff:fe0e:fd06 on eth0.*.
Sep 20 14:26:50 helena avahi-daemon[5136]: Registering new address record for 192.168.0.151 on eth0.IPv4.
Sep 20 14:26:50 helena avahi-daemon[5136]: Registering HINFO record with values 'I686'/'LINUX'.
Sep 20 14:26:50 helena apmd[5158]: apmd 3.2.1 interfacing with apm driver 1.16ac and APM BIOS 1.2
Sep 20 14:26:50 helena kernel: [   83.457087] ppdev: user-space parallel port driver
Sep 20 14:26:51 helena kernel: [   83.845882] audit(1221910011.088:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5193 profile="/usr/sbin/cupsd" namespace="default"
Sep 20 14:26:51 helena avahi-daemon[5136]: Server startup complete. Host name is helena.local. Local service cookie is 1591739092.
Sep 20 14:26:52 helena postfix/master[5285]: daemon started -- version 2.5.1, configuration /etc/postfix
Sep 20 14:26:55 helena dhcdbd: Started up.
Sep 20 14:26:57 helena NetworkManager: <debug> [1221910017.057843] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD_R/RW_MP7200A'). 
Sep 20 14:26:57 helena hcid[5570]: Bluetooth HCI daemon
Sep 20 14:26:57 helena kernel: [   90.035209] Bluetooth: Core ver 2.11
Sep 20 14:26:57 helena kernel: [   90.036695] NET: Registered protocol family 31
Sep 20 14:26:57 helena kernel: [   90.036708] Bluetooth: HCI device and connection manager initialized
Sep 20 14:26:57 helena kernel: [   90.036718] Bluetooth: HCI socket layer initialized
Sep 20 14:26:57 helena hcid[5570]: Starting SDP server
Sep 20 14:26:57 helena kernel: [   90.239435] Bluetooth: L2CAP ver 2.9
Sep 20 14:26:57 helena kernel: [   90.239449] Bluetooth: L2CAP socket layer initialized
Sep 20 14:26:57 helena hcid[5570]: Created local server at unix:abstract=/var/run/dbus-FhfYtHnU47,guid=cafe32eddbb720c4d0bb042848d4de01
Sep 20 14:26:57 helena kernel: [   90.292170] Bluetooth: RFCOMM socket layer initialized
Sep 20 14:26:57 helena kernel: [   90.292727] Bluetooth: RFCOMM TTY layer initialized
Sep 20 14:26:57 helena kernel: [   90.292738] Bluetooth: RFCOMM ver 1.8
Sep 20 14:26:57 helena audio[5591]: Bluetooth Audio daemon
Sep 20 14:26:57 helena input[5596]: Bluetooth Input daemon
Sep 20 14:26:57 helena audio[5591]: Unix socket created: 5
Sep 20 14:26:57 helena audio[5591]: audio.conf: Key file does not have key 'Enable'
Sep 20 14:26:57 helena audio[5591]: audio.conf: Key file does not have key 'Disable'
Sep 20 14:26:57 helena input[5596]: Registered input manager path:/org/bluez/input
Sep 20 14:26:57 helena NetworkManager: <debug> [1221910017.613956] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Sep 20 14:26:57 helena audio[5591]: add_service_record: got record id 0x10000
Sep 20 14:26:57 helena audio[5591]: audio.conf: Key file does not have key 'Disable'
Sep 20 14:26:57 helena audio[5591]: audio.conf: Key file does not have group 'A2DP'
Sep 20 14:26:57 helena last message repeated 3 times
Sep 20 14:26:57 helena audio[5591]: SEP 0x806d508 registered: type:0 codec:0 seid:1
Sep 20 14:26:57 helena audio[5591]: add_service_record: got record id 0x10001
Sep 20 14:26:57 helena audio[5591]: add_service_record: got record id 0x10002
Sep 20 14:26:57 helena audio[5591]: add_service_record: got record id 0x10003
Sep 20 14:26:57 helena audio[5591]: Registered manager path:/org/bluez/audio
Sep 20 14:27:00 helena anacron[5665]: Anacron 2.3 started on 2008-09-20
Sep 20 14:27:00 helena anacron[5665]: Normal exit (0 jobs run)
Sep 20 14:27:00 helena /usr/sbin/cron[5696]: (CRON) INFO (pidfile fd = 3)
Sep 20 14:27:00 helena /usr/sbin/cron[5697]: (CRON) STARTUP (fork ok)
Sep 20 14:27:00 helena /usr/sbin/cron[5697]: (CRON) INFO (Running @reboot jobs)
Sep 20 14:27:02 helena kernel: [   95.254034] [drm] Initialized drm 1.1.0 20060810
Sep 20 14:27:02 helena kernel: [   95.266127] [drm] Initialized r128 2.5.0 20030725 on minor 0
Sep 20 14:27:02 helena kernel: [   95.268134] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Sep 20 14:27:02 helena kernel: [   95.268173] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Sep 20 14:27:02 helena kernel: [   95.268219] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Sep 20 14:27:02 helena NetworkManager: <debug> [1221910022.534306] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_5046_drm_r128_card0'). 
Sep 20 14:28:15 helena hcid[5570]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Sep 20 14:28:15 helena hcid[5570]: Default authorization agent (:1.20, /org/bluez/auth) registered
Sep 20 14:28:27 helena NetworkManager: <info>  Updating allowed wireless network lists. 
Sep 20 14:28:27 helena NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Sep 20 14:29:43 helena init: tty4 main process (4818) killed by TERM signal
Sep 20 14:29:43 helena init: tty5 main process (4819) killed by TERM signal
Sep 20 14:29:43 helena init: tty2 main process (4823) killed by TERM signal
Sep 20 14:29:43 helena init: tty3 main process (4824) killed by TERM signal
Sep 20 14:29:43 helena init: tty6 main process (4826) killed by TERM signal
Sep 20 14:29:43 helena init: tty1 main process (5828) killed by TERM signal
Sep 20 14:29:45 helena avahi-daemon[5136]: Got SIGTERM, quitting.
Sep 20 14:29:45 helena avahi-daemon[5136]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.151.
Sep 20 14:29:45 helena postfix/master[5285]: terminating on signal 15
Sep 20 14:29:47 helena kernel: [  260.489028] ip6_tables: (C) 2000-2006 Netfilter Core Team
Sep 20 14:29:49 helena exiting on signal 15
Sep 20 14:52:19 helena syslogd 1.5.0#1ubuntu1: restart.
Sep 20 14:52:19 helena kernel: Inspecting /boot/System.map-2.6.24-19-generic
Sep 20 14:52:19 helena kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Sep 20 14:52:19 helena kernel: Symbols match kernel version 2.6.24.
Sep 20 14:52:20 helena kernel: Loaded 15236 symbols from 72 modules.
Sep 20 14:52:20 helena kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 20 14:52:20 helena kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 20 14:52:20 helena kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Sep 20 14:52:20 helena kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 20 14:52:20 helena kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Sep 20 14:52:20 helena kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Sep 20 14:52:20 helena kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Sep 20 14:52:20 helena kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Sep 20 14:52:20 helena kernel: [    0.000000] 0MB HIGHMEM available.
Sep 20 14:52:20 helena kernel: [    0.000000] 512MB LOWMEM available.
Sep 20 14:52:20 helena kernel: [    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
Sep 20 14:52:20 helena kernel: [    0.000000] Zone PFN ranges:
Sep 20 14:52:20 helena kernel: [    0.000000]   DMA             0 ->     4096
Sep 20 14:52:20 helena kernel: [    0.000000]   Normal       4096 ->   131072
Sep 20 14:52:20 helena kernel: [    0.000000]   HighMem    131072 ->   131072
Sep 20 14:52:20 helena kernel: [    0.000000] Movable zone start PFN for each node
Sep 20 14:52:20 helena kernel: [    0.000000] early_node_map[1] active PFN ranges
Sep 20 14:52:20 helena kernel: [    0.000000]     0:        0 ->   131072
Sep 20 14:52:20 helena kernel: [    0.000000] On node 0 totalpages: 131072
Sep 20 14:52:20 helena kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep 20 14:52:20 helena kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 20 14:52:20 helena kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Sep 20 14:52:20 helena kernel: [    0.000000]   Normal zone: 992 pages used for memmap
Sep 20 14:52:20 helena kernel: [    0.000000]   Normal zone: 125984 pages, LIFO batch:31
Sep 20 14:52:20 helena kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Sep 20 14:52:20 helena kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Sep 20 14:52:20 helena kernel: [    0.000000] DMI 2.2 present.
Sep 20 14:52:20 helena kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
Sep 20 14:52:20 helena kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Sep 20 14:52:20 helena kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Sep 20 14:52:20 helena kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130048
Sep 20 14:52:20 helena kernel: [    0.000000] Kernel command line: root=UUID=ebc88406-1be8-4eb1-899d-788a5cfc5a92 ro splash acpi=off apm=power_off
Sep 20 14:52:20 helena kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Sep 20 14:52:20 helena kernel: [    0.000000] mapped APIC to ffffb000 (0140d000)
Sep 20 14:52:20 helena kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 20 14:52:20 helena kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 20 14:52:20 helena kernel: [    0.000000] Initializing CPU#0
Sep 20 14:52:20 helena kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Sep 20 14:52:20 helena kernel: [    0.000000] Detected 733.370 MHz processor.
Sep 20 14:52:20 helena kernel: [   18.978473] Console: colour VGA+ 80x25
Sep 20 14:52:20 helena kernel: [   18.978487] console [tty0] enabled
Sep 20 14:52:20 helena kernel: [   18.980714] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 20 14:52:20 helena kernel: [   18.981903] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 20 14:52:20 helena kernel: [   19.034640] Memory: 507400k/524288k available (2177k kernel code, 16376k reserved, 1006k data, 368k init, 0k highmem)
Sep 20 14:52:20 helena kernel: [   19.034745] virtual kernel memory layout:
Sep 20 14:52:20 helena kernel: [   19.034748]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Sep 20 14:52:20 helena kernel: [   19.034752]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep 20 14:52:20 helena kernel: [   19.034756]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Sep 20 14:52:20 helena kernel: [   19.034760]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
Sep 20 14:52:20 helena kernel: [   19.034763]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Sep 20 14:52:20 helena kernel: [   19.034767]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Sep 20 14:52:20 helena kernel: [   19.034771]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Sep 20 14:52:20 helena kernel: [   19.035239] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Sep 20 14:52:20 helena kernel: [   19.035439] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Sep 20 14:52:20 helena kernel: [   19.115539] Calibrating delay using timer specific routine.. 1468.87 BogoMIPS (lpj=2937757)
Sep 20 14:52:20 helena kernel: [   19.115716] Security Framework initialized
Sep 20 14:52:20 helena kernel: [   19.115793] SELinux:  Disabled at boot.
Sep 20 14:52:20 helena kernel: [   19.115884] AppArmor: AppArmor initialized
Sep 20 14:52:20 helena kernel: [   19.115952] Failure registering capabilities with primary security module.
Sep 20 14:52:20 helena kernel: [   19.116034] Mount-cache hash table entries: 512
Sep 20 14:52:20 helena kernel: [   19.116372] Initializing cgroup subsys ns
Sep 20 14:52:20 helena kernel: [   19.116441] Initializing cgroup subsys cpuacct
Sep 20 14:52:20 helena kernel: [   19.116520] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
Sep 20 14:52:20 helena kernel: [   19.116549] CPU: L1 I cache: 16K, L1 D cache: 16K
Sep 20 14:52:20 helena kernel: [   19.116652] CPU: L2 cache: 256K
Sep 20 14:52:20 helena kernel: [   19.116717] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
Sep 20 14:52:20 helena kernel: [   19.116741] Compat vDSO mapped to ffffe000.
Sep 20 14:52:20 helena kernel: [   19.116830] Checking 'hlt' instruction... OK.
Sep 20 14:52:20 helena kernel: [   19.132225] SMP alternatives: switching to UP code
Sep 20 14:52:20 helena kernel: [   19.135802] Freeing SMP alternatives: 11k freed
Sep 20 14:52:20 helena kernel: [   19.136210] Early unpacking initramfs... done
Sep 20 14:52:20 helena kernel: [   20.105703] CPU0: Intel Pentium III (Coppermine) stepping 03
Sep 20 14:52:20 helena kernel: [   20.105907] SMP motherboard not detected.
Sep 20 14:52:20 helena kernel: [   20.105969] Local APIC not detected. Using dummy APIC emulation.
Sep 20 14:52:20 helena kernel: [   20.106175] Brought up 1 CPUs
Sep 20 14:52:20 helena kernel: [   20.106283] CPU0 attaching sched-domain:
Sep 20 14:52:20 helena kernel: [   20.106291]  domain 0: span 01
Sep 20 14:52:20 helena kernel: [   20.106297]   groups: 01
Sep 20 14:52:20 helena kernel: [   20.106872] net_namespace: 64 bytes
Sep 20 14:52:20 helena kernel: [   20.106957] Booting paravirtualized kernel on bare hardware
Sep 20 14:52:20 helena kernel: [   20.108642] Time: 11:50:56  Date: 09/20/08
Sep 20 14:52:20 helena kernel: [   20.108789] NET: Registered protocol family 16
Sep 20 14:52:20 helena kernel: [   20.109479] EISA bus registered
Sep 20 14:52:20 helena kernel: [   20.142267] PCI: PCI BIOS revision 2.10 entry at 0xfb1f0, last bus=1
Sep 20 14:52:20 helena kernel: [   20.142338] PCI: Using configuration type 1
Sep 20 14:52:20 helena kernel: [   20.142426] Setting up standard PCI resources
Sep 20 14:52:20 helena kernel: [   20.145487] ACPI: Interpreter disabled.
Sep 20 14:52:20 helena kernel: [   20.145561] Linux Plug and Play Support v0.97 (c) Adam Belay
Sep 20 14:52:20 helena kernel: [   20.145715] pnp: PnP ACPI: disabled
Sep 20 14:52:20 helena kernel: [   20.145785] PnPBIOS: Scanning system for PnP BIOS support...
Sep 20 14:52:20 helena kernel: [   20.146214] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbc20
Sep 20 14:52:20 helena kernel: [   20.146287] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbc50, dseg 0xf0000
Sep 20 14:52:20 helena kernel: [   20.149108] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
Sep 20 14:52:20 helena kernel: [   20.149883] PCI: Probing PCI hardware
Sep 20 14:52:20 helena kernel: [   20.149952] PCI: Probing PCI hardware (bus 00)
Sep 20 14:52:20 helena kernel: [   20.150403] PCI quirk: region 4000-40ff claimed by vt82c586 ACPI
Sep 20 14:52:20 helena kernel: [   20.150474] PCI quirk: region 5000-500f claimed by vt82c686 SMB
Sep 20 14:52:20 helena kernel: [   20.215353] NET: Registered protocol family 8
Sep 20 14:52:20 helena kernel: [   20.215428] NET: Registered protocol family 20
Sep 20 14:52:20 helena kernel: [   20.215700] AppArmor: AppArmor Filesystem Enabled
Sep 20 14:52:20 helena kernel: [   20.215891] system 00:07: iomem range 0x0-0x9ffff could not be reserved
Sep 20 14:52:20 helena kernel: [   20.215962] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
Sep 20 14:52:20 helena kernel: [   20.216043] system 00:07: iomem range 0x100000-0x1fffffff could not be reserved
Sep 20 14:52:20 helena kernel: [   20.216136] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
Sep 20 14:52:20 helena kernel: [   20.216205] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
Sep 20 14:52:20 helena kernel: [   20.216273] system 00:08: iomem range 0xf8000-0xfbfff could not be reserved
Sep 20 14:52:20 helena kernel: [   20.216342] system 00:08: iomem range 0xfc000-0xfffff could not be reserved
Sep 20 14:52:20 helena kernel: [   20.217603] PCI: Bridge: 0000:00:01.0
Sep 20 14:52:20 helena kernel: [   20.217670]   IO window: 9000-9fff
Sep 20 14:52:20 helena kernel: [   20.217735]   MEM window: e0000000-e1ffffff
Sep 20 14:52:20 helena kernel: [   20.217798]   PREFETCH window: dc000000-dfffffff
Sep 20 14:52:20 helena kernel: [   20.217878] PCI: Setting latency timer of device 0000:00:01.0 to 64
Sep 20 14:52:20 helena kernel: [   20.217912] NET: Registered protocol family 2
Sep 20 14:52:20 helena kernel: [   20.219332] Time: tsc clocksource has been installed.
Sep 20 14:52:20 helena kernel: [   20.251552] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
Sep 20 14:52:20 helena kernel: [   20.252359] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Sep 20 14:52:20 helena kernel: [   20.255193] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 20 14:52:20 helena kernel: [   20.258459] TCP: Hash tables configured (established 65536 bind 65536)
Sep 20 14:52:20 helena kernel: [   20.258546] TCP reno registered
Sep 20 14:52:20 helena kernel: [   20.267793] checking if image is initramfs... it is
Sep 20 14:52:20 helena kernel: [   22.100675] Freeing initrd memory: 7735k freed
Sep 20 14:52:20 helena kernel: [   22.102256] audit: initializing netlink socket (disabled)
Sep 20 14:52:20 helena kernel: [   22.102368] audit(1221911458.068:1): initialized
Sep 20 14:52:20 helena kernel: [   22.108710] VFS: Disk quotas dquot_6.5.1
Sep 20 14:52:20 helena kernel: [   22.109043] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 20 14:52:20 helena kernel: [   22.109736] io scheduler noop registered
Sep 20 14:52:20 helena kernel: [   22.109808] io scheduler anticipatory registered
Sep 20 14:52:20 helena kernel: [   22.109871] io scheduler deadline registered
Sep 20 14:52:20 helena kernel: [   22.109973] io scheduler cfq registered (default)
Sep 20 14:52:20 helena kernel: [   22.110066] PCI: VIA PCI bridge detected. Disabling DAC.
Sep 20 14:52:20 helena kernel: [   22.110132] PCI: Disabling Via external APIC routing
Sep 20 14:52:20 helena kernel: [   22.110236] Boot video device is 0000:01:00.0
Sep 20 14:52:20 helena kernel: [   22.110906] isapnp: Scanning for PnP cards...
Sep 20 14:52:20 helena kernel: [   22.465804] isapnp: No Plug & Play device found
Sep 20 14:52:20 helena kernel: [   22.563410] Real Time Clock Driver v1.12ac
Sep 20 14:52:20 helena kernel: [   22.563686] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Sep 20 14:52:20 helena kernel: [   22.564024] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 20 14:52:20 helena kernel: [   22.566084] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 20 14:52:20 helena kernel: [   22.568392] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Sep 20 14:52:20 helena kernel: [   22.568685] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Sep 20 14:52:20 helena kernel: [   22.569059] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
Sep 20 14:52:20 helena kernel: [   22.569128] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Sep 20 14:52:20 helena kernel: [   22.569482] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 20 14:52:20 helena kernel: [   22.579210] mice: PS/2 mouse device common for all mice
Sep 20 14:52:20 helena kernel: [   22.579619] EISA: Probing bus 0 at eisa.0
Sep 20 14:52:20 helena kernel: [   22.579712] Cannot allocate resource for EISA slot 4
Sep 20 14:52:20 helena kernel: [   22.579776] Cannot allocate resource for EISA slot 5
Sep 20 14:52:20 helena kernel: [   22.579856] EISA: Detected 0 cards.
Sep 20 14:52:20 helena kernel: [   22.579920] cpuidle: using governor ladder
Sep 20 14:52:20 helena kernel: [   22.579981] cpuidle: using governor menu
Sep 20 14:52:20 helena kernel: [   22.580491] NET: Registered protocol family 1
Sep 20 14:52:20 helena kernel: [   22.580633] Using IPI No-Shortcut mode
Sep 20 14:52:20 helena kernel: [   22.580772] registered taskstats version 1
Sep 20 14:52:20 helena kernel: [   22.581046]   Magic number: 8:474:833
Sep 20 14:52:20 helena kernel: [   22.581314] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 20 14:52:20 helena kernel: [   22.581380] EDD information not available.
Sep 20 14:52:20 helena kernel: [   22.582129] Freeing unused kernel memory: 368k freed
Sep 20 14:52:20 helena kernel: [   22.602194] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Sep 20 14:52:20 helena kernel: [   24.288215] fuse init (API version 7.9)
Sep 20 14:52:20 helena kernel: [   24.377599] thermal: Unknown symbol acpi_processor_set_thermal_limit
Sep 20 14:52:20 helena kernel: [   25.402193] SCSI subsystem initialized
Sep 20 14:52:20 helena kernel: [   25.466538] usbcore: registered new interface driver usbfs
Sep 20 14:52:20 helena kernel: [   25.466604] usbcore: registered new interface driver hub
Sep 20 14:52:20 helena kernel: [   25.515168] usbcore: registered new device driver usb
Sep 20 14:52:20 helena kernel: [   25.530400] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Sep 20 14:52:20 helena kernel: [   25.530506] 8139cp 0000:00:10.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Sep 20 14:52:20 helena kernel: [   25.530514] 8139cp 0000:00:10.0: Try the "8139too" driver instead.
Sep 20 14:52:20 helena kernel: [   25.552650] 8139too Fast Ethernet driver 0.9.28
Sep 20 14:52:20 helena kernel: [   25.586960] eth0: RealTek RTL8139 at 0xc000, 00:10:a7:0e:fd:06, IRQ 11
Sep 20 14:52:20 helena kernel: [   25.586975] eth0:  Identified 8139 chip type 'RTL-8139C'
Sep 20 14:52:20 helena kernel: [   25.666401] USB Universal Host Controller Interface driver v3.0
Sep 20 14:52:20 helena kernel: [   25.666617] uhci_hcd 0000:00:07.2: UHCI Host Controller
Sep 20 14:52:20 helena kernel: [   25.667112] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Sep 20 14:52:20 helena kernel: [   25.667156] uhci_hcd 0000:00:07.2: irq 5, io base 0x0000a400
Sep 20 14:52:20 helena kernel: [   25.667511] usb usb1: configuration #1 chosen from 1 choice
Sep 20 14:52:20 helena kernel: [   25.667585] hub 1-0:1.0: USB hub found
Sep 20 14:52:20 helena kernel: [   25.667603] hub 1-0:1.0: 2 ports detected
Sep 20 14:52:20 helena kernel: [   25.714340] libata version 3.00 loaded.
Sep 20 14:52:20 helena kernel: [   25.770628] uhci_hcd 0000:00:07.3: UHCI Host Controller
Sep 20 14:52:20 helena kernel: [   25.770701] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
Sep 20 14:52:20 helena kernel: [   25.770738] uhci_hcd 0000:00:07.3: irq 5, io base 0x0000a800
Sep 20 14:52:20 helena kernel: [   25.771050] usb usb2: configuration #1 chosen from 1 choice
Sep 20 14:52:20 helena kernel: [   25.771118] hub 2-0:1.0: USB hub found
Sep 20 14:52:20 helena kernel: [   25.771136] hub 2-0:1.0: 2 ports detected
Sep 20 14:52:20 helena kernel: [   25.892376] Floppy drive(s): fd0 is 1.44M
Sep 20 14:52:20 helena kernel: [   25.910202] FDC 0 is a post-1991 82077
Sep 20 14:52:20 helena kernel: [   25.936670] pata_via 0000:00:07.1: version 0.3.3
Sep 20 14:52:20 helena kernel: [   25.962299] scsi0 : pata_via
Sep 20 14:52:20 helena kernel: [   25.987046] scsi1 : pata_via
Sep 20 14:52:20 helena kernel: [   25.987189] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xa000 irq 14
Sep 20 14:52:20 helena kernel: [   25.987198] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xa008 irq 15
Sep 20 14:52:20 helena kernel: [   26.266248] usb 2-1: new low speed USB device using uhci_hcd and address 2
Sep 20 14:52:20 helena kernel: [   26.314740] ata1.00: ATA-6: Maxtor 32049H3, BAC51KJ0, max UDMA/100
Sep 20 14:52:20 helena kernel: [   26.314756] ata1.00: 40021632 sectors, multi 16: LBA 
Sep 20 14:52:20 helena kernel: [   26.314820] ata1.01: ATAPI: MATSHITADVD-ROM SR-8585, 1S29, max UDMA/33
Sep 20 14:52:20 helena kernel: [   26.330701] ata1.00: configured for UDMA/66
Sep 20 14:52:20 helena kernel: [   26.447859] usb 2-1: configuration #1 chosen from 1 choice
Sep 20 14:52:20 helena kernel: [   26.494504] ata1.01: configured for UDMA/33
Sep 20 14:52:20 helena kernel: [   26.650389] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Sep 20 14:52:20 helena kernel: [   26.650405] ata2: failed to recover some devices, retrying in 5 secs
Sep 20 14:52:20 helena kernel: [   26.690179] usb 2-2: new full speed USB device using uhci_hcd and address 3
Sep 20 14:52:20 helena kernel: [   26.843696] usb 2-2: configuration #1 chosen from 1 choice
Sep 20 14:52:20 helena kernel: [   26.845562] hub 2-2:1.0: USB hub found
Sep 20 14:52:20 helena kernel: [   26.847537] hub 2-2:1.0: 4 ports detected
Sep 20 14:52:20 helena kernel: [   27.590821] usbcore: registered new interface driver hiddev
Sep 20 14:52:20 helena kernel: [   27.642538] input: Microsoft Microsoft USB Wireless Mouse as /devices/pci0000:00/0000:00:07.3/usb2/2-1/2-1:1.0/input/input2
Sep 20 14:52:20 helena kernel: [   27.654039] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:07.3-1
Sep 20 14:52:20 helena kernel: [   27.654092] usbcore: registered new interface driver usbhid
Sep 20 14:52:20 helena kernel: [   27.654103] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Sep 20 14:52:20 helena kernel: [   31.809351] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Sep 20 14:52:20 helena kernel: [   31.809367] ata2: failed to recover some devices, retrying in 5 secs
Sep 20 14:52:20 helena kernel: [   36.968367] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x1)
Sep 20 14:52:20 helena kernel: [   36.968383] ata2: failed to recover some devices, retrying in 5 secs
Sep 20 14:52:20 helena kernel: [   42.291411] ata2.00: ATAPI: RICOH   CD-R/RW MP7200A, 1.20, max UDMA/33
Sep 20 14:52:20 helena kernel: [   42.463381] ata2.00: configured for UDMA/33
Sep 20 14:52:20 helena kernel: [   42.463706] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 32049H3   BAC5 PQ: 0 ANSI: 5
Sep 20 14:52:20 helena kernel: [   42.465658] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-ROM SR-8585  1S29 PQ: 0 ANSI: 5
Sep 20 14:52:20 helena kernel: [   42.467567] scsi 1:0:0:0: CD-ROM            RICOH    CD-R/RW MP7200A  1.20 PQ: 0 ANSI: 5
Sep 20 14:52:20 helena kernel: [   42.516495] Driver 'sd' needs updating - please use bus_type methods
Sep 20 14:52:20 helena kernel: [   42.520926] sd 0:0:0:0: [sda] 40021632 512-byte hardware sectors (20491 MB)
Sep 20 14:52:20 helena kernel: [   42.520975] sd 0:0:0:0: [sda] Write Protect is off
Sep 20 14:52:20 helena kernel: [   42.520984] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 20 14:52:20 helena kernel: [   42.521044] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 20 14:52:20 helena kernel: [   42.521193] sd 0:0:0:0: [sda] 40021632 512-byte hardware sectors (20491 MB)
Sep 20 14:52:20 helena kernel: [   42.521227] sd 0:0:0:0: [sda] Write Protect is off
Sep 20 14:52:20 helena kernel: [   42.521235] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 20 14:52:20 helena kernel: [   42.521291] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 20 14:52:20 helena kernel: [   42.521304]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Sep 20 14:52:20 helena kernel: [   42.541338]  sda1 sda2 < sda5 sda6 >
Sep 20 14:52:20 helena kernel: [   42.568504] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 20 14:52:20 helena kernel: [   42.591798] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 20 14:52:20 helena kernel: [   42.591861] sr 0:0:1:0: Attached scsi generic sg1 type 5
Sep 20 14:52:20 helena kernel: [   42.591936] scsi 1:0:0:0: Attached scsi generic sg2 type 5
Sep 20 14:52:20 helena kernel: [   42.592364] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
Sep 20 14:52:20 helena kernel: [   42.592376] Uniform CD-ROM driver Revision: 3.20
Sep 20 14:52:20 helena kernel: [   42.592486] sr 0:0:1:0: Attached scsi CD-ROM sr0
Sep 20 14:52:20 helena kernel: [   42.597203] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Sep 20 14:52:20 helena kernel: [   42.597375] sr 1:0:0:0: Attached scsi CD-ROM sr1
Sep 20 14:52:20 helena kernel: [   43.833718] Attempting manual resume
Sep 20 14:52:20 helena kernel: [   43.833731] swsusp: Resume From Partition 8:6
Sep 20 14:52:20 helena kernel: [   43.833736] PM: Checking swsusp image.
Sep 20 14:52:20 helena kernel: [   43.847420] PM: Resume from disk failed.
Sep 20 14:52:20 helena kernel: [   43.943187] kjournald starting.  Commit interval 5 seconds
Sep 20 14:52:20 helena kernel: [   43.943225] EXT3-fs: mounted filesystem with ordered data mode.
Sep 20 14:52:20 helena kernel: [   59.692197] input: PC Speaker as /devices/platform/pcspkr/input/input3
Sep 20 14:52:20 helena kernel: [   61.531636] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 20 14:52:20 helena kernel: [   61.610541] parport_pc: VIA 686A/8231 detected
Sep 20 14:52:20 helena kernel: [   61.610553] parport_pc: probing current configuration
Sep 20 14:52:20 helena kernel: [   61.610578] parport_pc: Current parallel port base: 0x378
Sep 20 14:52:20 helena kernel: [   61.610640] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Sep 20 14:52:20 helena kernel: [   61.661634] Linux agpgart interface v0.102
Sep 20 14:52:20 helena kernel: [   61.699775] parport_pc: VIA parallel port: io=0x378, irq=7
Sep 20 14:52:20 helena kernel: [   61.742171] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep 20 14:52:20 helena kernel: [   61.979525] agpgart: Detected VIA Apollo Pro 133 chipset
Sep 20 14:52:20 helena kernel: [   61.983270] agpgart: AGP aperture is 64M @ 0xd8000000
Sep 20 14:52:20 helena kernel: [   62.131813] via686a 0000:00:07.4: base address not set - upgrade BIOS or use force_addr=0xaddr
Sep 20 14:52:20 helena kernel: [   63.069765] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep 20 14:52:20 helena kernel: [   65.623837] NET: Registered protocol family 10
Sep 20 14:52:20 helena kernel: [   65.624539] lo: Disabled Privacy Extensions
Sep 20 14:52:20 helena kernel: [   65.903807] PCI: Setting latency timer of device 0000:00:07.5 to 64
Sep 20 14:52:20 helena kernel: [   69.459558] lp0: using parport0 (interrupt-driven).
Sep 20 14:52:20 helena kernel: [   69.502026] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Sep 20 14:52:20 helena kernel: [   69.687369] Adding 1003988k swap on /dev/sda6.  Priority:-1 extents:1 across:1003988k
Sep 20 14:52:20 helena kernel: [   70.340456] EXT3 FS on sda1, internal journal
Sep 20 14:52:20 helena kernel: [   70.639707] device-mapper: uevent: version 1.0.3
Sep 20 14:52:20 helena kernel: [   70.639794] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Sep 20 14:52:20 helena kernel: [   76.272622] eth0: no IPv6 routers present
Sep 20 14:52:20 helena kernel: [   99.290399] kjournald starting.  Commit interval 5 seconds
Sep 20 14:52:20 helena kernel: [   99.290790] EXT3 FS on sda5, internal journal
Sep 20 14:52:20 helena kernel: [   99.290803] EXT3-fs: mounted filesystem with ordered data mode.
Sep 20 14:52:20 helena kernel: [  100.619899] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 20 14:52:20 helena kernel: [  102.028985] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
Sep 20 14:52:20 helena kernel: [  102.029197] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
Sep 20 14:52:20 helena kernel: [  102.029926] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
Sep 20 14:52:20 helena kernel: [  102.030249] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
Sep 20 14:52:20 helena NetworkManager: <info>  starting... 
Sep 20 14:52:20 helena avahi-daemon[5318]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Sep 20 14:52:20 helena avahi-daemon[5318]: Successfully dropped root privileges.
Sep 20 14:52:20 helena avahi-daemon[5318]: avahi-daemon 0.6.22 starting up.
Sep 20 14:52:20 helena avahi-daemon[5318]: Successfully called chroot().
Sep 20 14:52:20 helena avahi-daemon[5318]: Successfully dropped remaining capabilities.
Sep 20 14:52:21 helena avahi-daemon[5318]: No service file found in /etc/avahi/services.
Sep 20 14:52:21 helena avahi-daemon[5318]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.151.
Sep 20 14:52:21 helena avahi-daemon[5318]: New relevant interface eth0.IPv4 for mDNS.
Sep 20 14:52:21 helena avahi-daemon[5318]: Network interface enumeration completed.
Sep 20 14:52:21 helena avahi-daemon[5318]: Registering new address record for fe80::210:a7ff:fe0e:fd06 on eth0.*.
Sep 20 14:52:21 helena avahi-daemon[5318]: Registering new address record for 192.168.0.151 on eth0.IPv4.
Sep 20 14:52:21 helena avahi-daemon[5318]: Registering HINFO record with values 'I686'/'LINUX'.
Sep 20 14:52:21 helena apmd[5340]: apmd 3.2.1 interfacing with apm driver 1.16ac and APM BIOS 1.2
Sep 20 14:52:21 helena kernel: [  104.954253] ppdev: user-space parallel port driver
Sep 20 14:52:22 helena avahi-daemon[5318]: Server startup complete. Host name is helena.local. Local service cookie is 2413761295.
Sep 20 14:52:22 helena kernel: [  105.387576] audit(1221911542.228:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5375 profile="/usr/sbin/cupsd" namespace="default"
Sep 20 14:52:23 helena postfix/master[5467]: daemon started -- version 2.5.1, configuration /etc/postfix
Sep 20 14:52:26 helena dhcdbd: Started up.
Sep 20 14:52:28 helena NetworkManager: <debug> [1221911548.050552] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD_R/RW_MP7200A'). 
Sep 20 14:52:28 helena hcid[5754]: Bluetooth HCI daemon
Sep 20 14:52:28 helena kernel: [  111.470279] Bluetooth: Core ver 2.11
Sep 20 14:52:28 helena kernel: [  111.482062] NET: Registered protocol family 31
Sep 20 14:52:28 helena kernel: [  111.482076] Bluetooth: HCI device and connection manager initialized
Sep 20 14:52:28 helena kernel: [  111.482086] Bluetooth: HCI socket layer initialized
Sep 20 14:52:28 helena hcid[5754]: Starting SDP server
Sep 20 14:52:28 helena kernel: [  111.734120] Bluetooth: L2CAP ver 2.9
Sep 20 14:52:28 helena kernel: [  111.734136] Bluetooth: L2CAP socket layer initialized
Sep 20 14:52:28 helena hcid[5754]: Created local server at unix:abstract=/var/run/dbus-2INhXtPRIN,guid=c30a9e7011c1d883d044a9c548d4e3fc
Sep 20 14:52:28 helena NetworkManager: <debug> [1221911548.622748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Sep 20 14:52:28 helena kernel: [  111.799380] Bluetooth: RFCOMM socket layer initialized
Sep 20 14:52:28 helena kernel: [  111.799428] Bluetooth: RFCOMM TTY layer initialized
Sep 20 14:52:28 helena kernel: [  111.799434] Bluetooth: RFCOMM ver 1.8
Sep 20 14:52:28 helena audio[5775]: Bluetooth Audio daemon
Sep 20 14:52:28 helena input[5781]: Bluetooth Input daemon
Sep 20 14:52:28 helena input[5781]: Registered input manager path:/org/bluez/input
Sep 20 14:52:28 helena audio[5775]: Unix socket created: 5
Sep 20 14:52:28 helena audio[5775]: audio.conf: Key file does not have key 'Enable'
Sep 20 14:52:28 helena audio[5775]: audio.conf: Key file does not have key 'Disable'
Sep 20 14:52:28 helena audio[5775]: add_service_record: got record id 0x10000
Sep 20 14:52:28 helena audio[5775]: audio.conf: Key file does not have key 'Disable'
Sep 20 14:52:28 helena audio[5775]: audio.conf: Key file does not have group 'A2DP'
Sep 20 14:52:28 helena last message repeated 3 times
Sep 20 14:52:28 helena audio[5775]: SEP 0x806d508 registered: type:0 codec:0 seid:1
Sep 20 14:52:28 helena audio[5775]: add_service_record: got record id 0x10001
Sep 20 14:52:28 helena audio[5775]: add_service_record: got record id 0x10002
Sep 20 14:52:28 helena audio[5775]: add_service_record: got record id 0x10003
Sep 20 14:52:28 helena audio[5775]: Registered manager path:/org/bluez/audio
Sep 20 14:52:30 helena anacron[5849]: Anacron 2.3 started on 2008-09-20
Sep 20 14:52:30 helena anacron[5849]: Normal exit (0 jobs run)
Sep 20 14:52:30 helena /usr/sbin/cron[5880]: (CRON) INFO (pidfile fd = 3)
Sep 20 14:52:30 helena /usr/sbin/cron[5881]: (CRON) STARTUP (fork ok)
Sep 20 14:52:30 helena /usr/sbin/cron[5881]: (CRON) INFO (Running @reboot jobs)
Sep 20 14:52:32 helena kernel: [  115.194670] [drm] Initialized drm 1.1.0 20060810
Sep 20 14:52:32 helena kernel: [  115.217512] [drm] Initialized r128 2.5.0 20030725 on minor 0
Sep 20 14:52:32 helena kernel: [  115.219460] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Sep 20 14:52:32 helena kernel: [  115.219500] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Sep 20 14:52:32 helena kernel: [  115.219547] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Sep 20 14:52:32 helena NetworkManager: <debug> [1221911552.077775] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_5046_drm_r128_card0'). 
Sep 20 14:53:16 helena hcid[5754]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Sep 20 14:53:16 helena hcid[5754]: Default authorization agent (:1.20, /org/bluez/auth) registered
Sep 20 14:53:30 helena NetworkManager: <info>  Updating allowed wireless network lists. 
Sep 20 14:53:30 helena NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Sep 20 14:56:01 helena ntpd[3756]: synchronized to 91.189.94.4, stratum 2
Sep 20 14:56:01 helena ntpd[3756]: kernel time sync status change 0001
Sep 20 14:57:02 helena kernel: [  385.663412] usb 2-2.1: new full speed USB device using uhci_hcd and address 4
Sep 20 14:57:02 helena kernel: [  385.788509] usb 2-2.1: configuration #1 chosen from 1 choice
Sep 20 14:57:02 helena NetworkManager: <debug> [1221911822.727612] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 14:57:03 helena NetworkManager: <debug> [1221911823.066386] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:08:49 helena kernel: [ 1092.916288] usb 2-2.1: USB disconnect, address 4
Sep 20 15:08:50 helena NetworkManager: <debug> [1221912530.250596] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:08:50 helena NetworkManager: <debug> [1221912530.256087] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:17:02 helena /USR/SBIN/CRON[6814]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 20 15:18:38 helena kernel: [ 1681.462636] usb 2-2.1: new full speed USB device using uhci_hcd and address 5
Sep 20 15:18:38 helena kernel: [ 1681.599806] usb 2-2.1: configuration #1 chosen from 1 choice
Sep 20 15:18:38 helena NetworkManager: <debug> [1221913118.842960] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:18:39 helena NetworkManager: <debug> [1221913119.658984] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:19:26 helena kernel: [ 1729.579643] usb 2-2.1: USB disconnect, address 5
Sep 20 15:19:26 helena NetworkManager: <debug> [1221913166.867843] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:19:26 helena NetworkManager: <debug> [1221913166.876103] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:20:13 helena kernel: [ 1776.181283] usb 2-2.1: new full speed USB device using uhci_hcd and address 6
Sep 20 15:20:13 helena kernel: [ 1776.317453] usb 2-2.1: configuration #1 chosen from 1 choice
Sep 20 15:20:13 helena NetworkManager: <debug> [1221913213.584839] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:20:13 helena NetworkManager: <debug> [1221913213.891768] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:27:40 helena kernel: [ 2223.326413] usb 2-2.1: USB disconnect, address 6
Sep 20 15:27:40 helena NetworkManager: <debug> [1221913660.885790] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:27:40 helena NetworkManager: <debug> [1221913660.892088] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:28:28 helena kernel: [ 2271.342457] usb 2-2.1: new full speed USB device using uhci_hcd and address 7
Sep 20 15:28:28 helena kernel: [ 2271.478647] usb 2-2.1: configuration #1 chosen from 1 choice
Sep 20 15:28:28 helena NetworkManager: <debug> [1221913708.867701] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:28:29 helena NetworkManager: <debug> [1221913709.305746] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:45:17 helena kernel: [ 3279.783267] usb 2-2.1: USB disconnect, address 7
Sep 20 15:45:17 helena NetworkManager: <debug> [1221914717.485917] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:45:17 helena NetworkManager: <debug> [1221914717.496243] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:46:00 helena kernel: [ 3323.157222] usb 2-2.1: new full speed USB device using uhci_hcd and address 8
Sep 20 15:46:00 helena kernel: [ 3323.295412] usb 2-2.1: configuration #1 chosen from 1 choice
Sep 20 15:46:00 helena NetworkManager: <debug> [1221914760.946996] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:46:01 helena NetworkManager: <debug> [1221914761.479939] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:50:57 helena kernel: [ 3619.610010] usb 2-2.1: USB disconnect, address 8
Sep 20 15:50:57 helena NetworkManager: <debug> [1221915057.368718] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:50:57 helena NetworkManager: <debug> [1221915057.376091] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:51:46 helena kernel: [ 3668.554717] usb 2-2.1: new full speed USB device using uhci_hcd and address 9
Sep 20 15:51:46 helena kernel: [ 3668.690828] usb 2-2.1: configuration #1 chosen from 1 choice
Sep 20 15:51:46 helena NetworkManager: <debug> [1221915106.429915] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:51:46 helena NetworkManager: <debug> [1221915106.829917] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:52:46 helena kernel: [ 3729.260434] usb 2-2.1: USB disconnect, address 9
Sep 20 15:52:47 helena NetworkManager: <debug> [1221915167.074485] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 15:52:47 helena NetworkManager: <debug> [1221915167.082041] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:53:41 helena kernel: [ 3783.356927] usb 2-2.1: new full speed USB device using uhci_hcd and address 10
Sep 20 15:53:41 helena kernel: [ 3783.494109] usb 2-2.1: configuration #1 chosen from 1 choice
Sep 20 15:53:41 helena NetworkManager: <debug> [1221915221.262099] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 15:53:41 helena NetworkManager: <debug> [1221915221.578797] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 16:03:51 helena kernel: [ 4393.560301] usb 2-2.1: USB disconnect, address 10
Sep 20 16:03:51 helena NetworkManager: <debug> [1221915831.511260] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial_if0'). 
Sep 20 16:03:51 helena NetworkManager: <debug> [1221915831.527941] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3058_noserial'). 
Sep 20 16:17:01 helena /USR/SBIN/CRON[8079]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 20 16:25:23 helena gdm[5819]: WARNING: gdm_slave_xioerror_handler: Vakava X-virhe – :0 käynnistetään uudelleen 
Sep 20 16:25:26 helena kernel: [ 5688.508298] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Sep 20 16:25:26 helena kernel: [ 5688.509048] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Sep 20 16:25:26 helena kernel: [ 5688.509389] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Sep 20 16:25:47 helena pulseaudio[8273]: pid.c: Stale PID file, overwriting.
Sep 20 16:25:53 helena hcid[5754]: Default passkey agent (:1.68, /org/bluez/passkey) registered
Sep 20 16:25:53 helena hcid[5754]: Default authorization agent (:1.68, /org/bluez/auth) registered
Sep 20 16:25:59 helena NetworkManager: <info>  Updating allowed wireless network lists. 
Sep 20 16:25:59 helena NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```

Xorg.0.log:
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux helena 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 20 16:25:25 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
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
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) Open APM successful
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0691 card 0000,0000 rev c4 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8598 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0686 card 1106,0000 rev 22 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 0000,0000 rev 10 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:07:4: chip 1106,3057 card 0000,0000 rev 30 class 06,00,00 hdr 00
(II) PCI: 00:07:5: chip 1106,3058 card 1106,4511 rev 20 class 04,01,00 hdr 00
(II) PCI: 00:0f:0: chip 127a,2014 card 122d,4055 rev 01 class 07,80,00 hdr 00
(II) PCI: 00:10:0: chip 10ec,8139 card 1429,d010 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5046 card 1002,0008 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0xdc000000/26, 0xe1000000/14, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdbffffff to 0xd7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[1] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[2] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[3] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[4] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[5] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[6] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[7] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[8] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[9] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[11] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[12] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[13] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[1] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[2] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[3] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[4] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[5] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[6] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[7] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[8] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[9] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[11] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[12] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[13] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[12] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[15] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[19] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched ati from file name ati.ids in autoconfig
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.1.0


	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset ATI Rage 128 Pro GL PF (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[12] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[15] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[19] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[22] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) R128(0): PCI bus 1 card 0 func 0
(II) R128(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) R128(0): Depth 24, (==) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 Pro GL PF (AGP)" (ChipID = 0x5046)
(--) R128(0): Linear framebuffer at 0xdc000000
(--) R128(0): MMIO registers at 0xe1000000
(--) R128(0): VideoRAM: 32768 kByte (64-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(II) R128(0): Primary Display == Type 3
(WW) R128(0): Can't determine panel dimensions, and none specified.
	Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=40000; xclk=12000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 32768 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level 2
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read successfully
(II) R128(0): Manufacturer: SAM  Model: c8  Serial#: 1146302775
(II) R128(0): Year: 2004  Week: 44
(II) R128(0): EDID Version: 1.3
(II) R128(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) R128(0): Sync:  Separate  Composite
(II) R128(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) R128(0): Gamma: 2.20
(II) R128(0): DPMS capabilities: Off; RGB/Color Display
(II) R128(0): First detailed timing is preferred mode
(II) R128(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) R128(0): blueX: 0.143 blueY: 0.102   whiteX: 0.318 whiteY: 0.339
(II) R128(0): Supported VESA Video Modes:
(II) R128(0): 720x400@70Hz
(II) R128(0): 640x480@60Hz
(II) R128(0): 640x480@67Hz
(II) R128(0): 640x480@72Hz
(II) R128(0): 640x480@75Hz
(II) R128(0): 800x600@56Hz
(II) R128(0): 800x600@60Hz
(II) R128(0): 800x600@72Hz
(II) R128(0): 800x600@75Hz
(II) R128(0): 832x624@75Hz
(II) R128(0): 1024x768@60Hz
(II) R128(0): 1024x768@70Hz
(II) R128(0): 1024x768@75Hz
(II) R128(0): 1280x1024@75Hz
(II) R128(0): Manufacturer's mask: 0
(II) R128(0): Supported Future Video Modes:
(II) R128(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) R128(0): Supported additional Video Mode:
(II) R128(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) R128(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) R128(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) R128(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) R128(0): Monitor name: SyncMaster
(II) R128(0): Serial No: HSHXA05168
(II) R128(0): EDID (in hex):
(II) R128(0): 	00ffffffffffff004c2dc80037315344
(II) R128(0): 	2c0e01036c221b782a6f8ba25a4d9424
(II) R128(0): 	1a5156bfef0081800101010101010101
(II) R128(0): 	010101010101302a009851002a403070
(II) R128(0): 	1300520e1100001e000000fd00384b1e
(II) R128(0): 	510e000a202020202020000000fc0053
(II) R128(0): 	796e634d61737465720a2020000000ff
(II) R128(0): 	00485348584130353136380a202000f6
(II) R128(0): EDID vendor "SAM", prod id 200
(II) R128(0): Using EDID range info for horizontal sync
(II) R128(0): Using EDID range info for vertical refresh
(II) R128(0): Printing DDC gathered Modelines:
(II) R128(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) R128(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) R128(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) R128(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) R128(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) R128(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) R128(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) R128(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) R128(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) R128(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) R128(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) R128(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) R128(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) R128(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) R128(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) R128(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(==) R128(0): Write-combining range (0xdc000000,0x2000000)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) R128(0): I2C device "DDC:ddc2" removed.
(EE) R128(0): No DFP detected
(II) R128(0): Configured Monitor: Using hsync range of 30.00-81.00 kHz
(II) R128(0): Configured Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) R128(0): Configured Monitor: Using maximum pixel clock of 140.00 MHz
(II) R128(0): Estimated virtual size for aspect ratio 1.2593 is 1280x1024
(II) R128(0): Clock range:  12.50 to 400.00 MHz
(II) R128(0): Not using default mode "640x350" (vrefresh out of range)
(II) R128(0): Not using default mode "320x175" (vrefresh out of range)
(II) R128(0): Not using default mode "640x400" (vrefresh out of range)
(II) R128(0): Not using default mode "320x200" (vrefresh out of range)
(II) R128(0): Not using default mode "720x400" (vrefresh out of range)
(II) R128(0): Not using default mode "360x200" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (vrefresh out of range)

(II) R128(0): Not using default mode "800x600" (vrefresh out of range)
(II) R128(0): Not using default mode "400x300" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1152x768" (vrefresh out of range)
(II) R128(0): Not using default mode "576x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1152x864" (vrefresh out of range)
(II) R128(0): Not using default mode "576x432" (vrefresh out of range)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1440x900" (width too large for virtual size)
(II) R128(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(--) R128(0): Virtual size is 1280x1024 (pitch 1280)
(**) R128(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) R128(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) R128(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) R128(0): *Driver mode "1280x1024": 109.0 MHz, 63.7 kHz, 59.9 Hz
(II) R128(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(**) R128(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) R128(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) R128(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) R128(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(**) R128(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) R128(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) R128(0): *Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(**) R128(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) R128(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) R128(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) R128(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) R128(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) R128(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) R128(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) R128(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "960x600"x60.0   96.58  960 1024 1128 1296  600 600 602 621 doublescan (74.5 kHz)
(**) R128(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) R128(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) R128(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) R128(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) R128(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) R128(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) R128(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) R128(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) R128(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) R128(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) R128(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) R128(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) R128(0): *Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) R128(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
(**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
(**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "840x525"x60.1   73.57  840 892 984 1128  525 525 527 543 doublescan (65.2 kHz)
(**) R128(0): *Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) R128(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
(**) R128(0): *Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(II) R128(0): Modeline "700x525"x70.0   75.50  700 732 828 980  525 525 527 550 doublescan +hsync +vsync (77.0 kHz)
(**) R128(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) R128(0): *Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
(**) R128(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) R128(0): *Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) R128(0): Modeline "720x450"x60.2   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync (56.9 kHz)
(**) R128(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) R128(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) R128(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) R128(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) R128(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) R128(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) R128(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) R128(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) R128(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) R128(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) R128(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) R128(0): *Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x400"x60.0   41.73  640 672 740 840  400 400 402 414 doublescan (49.7 kHz)
(**) R128(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) R128(0): *Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "640x384"x60.1   40.07  640 672 740 840  384 384 386 397 doublescan (47.7 kHz)
(**) R128(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) R128(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) R128(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) R128(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) R128(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) R128(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) R128(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) R128(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) R128(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) R128(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) R128(0): Display dimensions: (340, 270) mm
(**) R128(0): DPI set to (95, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe1000000 - 0xe1003fff (0x4000) MS[B]
	[1] 0	0	0xdc000000 - 0xdfffffff (0x4000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[7] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[8] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[9] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[14] 0	0	0x00009000 - 0x000090ff (0x100) IS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[21] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[25] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) R128(0): Write-combining range (0xdc000000,0x2000000)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
(II) R128(0): [drm] framebuffer handle = 0xdc000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(II) R128(0): [agp] Mode 0x1f000201 [AGP 0x1106/0x0691; Card 0x1002/0x5046]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II) R128(0): [agp] ring handle = 0xd8000000
(II) R128(0): [agp] Ring mapped at 0xb7a4d000
(II) R128(0): [agp] ring read ptr handle = 0xd8101000
(II) R128(0): [agp] Ring read ptr mapped at 0xb7a4c000
(II) R128(0): [agp] vertex/indirect buffers handle = 0xd8102000
(II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb577d000
(II) R128(0): [agp] AGP texture map handle = 0xd8302000
(II) R128(0): [agp] AGP Texture map mapped at 0xb529d000
(II) R128(0): [drm] register handle = 0xe1000000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (1280,4096)
(II) R128(0): Reserved area from (0,1024) to (1280,1026)
(II) R128(0): Largest offscreen area available: 1280 x 3070
(II) R128(0): Reserved back buffer from (0,1026) to (1280,2050)
(II) R128(0): Reserved depth buffer from (0,2050) to (1280,3075)
(II) R128(0): Reserved depth span from (0,3074) offset 0xf02800
(II) R128(0): Reserved 12288 kb for textures at offset 0x1400000
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		9 256x256 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 12300)
(II) R128(0): Largest offscreen area available: 1280 x 1019
(II) R128(0): DPMS enabled
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 10
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "fi"
(**) Generic Keyboard: XkbLayout: "fi"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
```

I saved them immediately after logging in after a crash like this occurred. I was browsing my photos in Gwenview when it happened. I use Ubuntu in Finnish, so if there's something in the logs you don't understand then feel free to ask me to translate it. At least I saw the following line in the syslog:
```
Sep 20 16:25:23 helena gdm[5819]: WARNING: gdm_slave_xioerror_handler: Vakava X-virhe – :0 käynnistetään uudelleen
```
Here "Vakava X-virhe – :0 käynnistetään uudelleen" means "Serious X error - :0 restarting".

Thanks in advance for further help! :)

---

### Post by Ingo88 on 2008-09-20
It happened again. This time I was also browsing photos in Gwenview (though I believe that's purely coincidental. see the first post of this thread). Here are the syslog entries from the few minutes around the crash:

```
Sep 20 17:52:19 helena -- MARK --
Sep 20 17:53:26 helena gdm[8119]: WARNING: gdm_slave_xioerror_handler: Vakava X-virhe – :0 käynnistetään uudelleen 
Sep 20 17:53:30 helena kernel: [10970.825378] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Sep 20 17:53:30 helena kernel: [10970.826106] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Sep 20 17:53:30 helena kernel: [10970.826446] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Sep 20 17:53:49 helena pulseaudio[9871]: pid.c: Stale PID file, overwriting.
Sep 20 17:53:59 helena hcid[5754]: Default passkey agent (:1.95, /org/bluez/passkey) registered
Sep 20 17:53:59 helena hcid[5754]: Default authorization agent (:1.95, /org/bluez/auth) registered
Sep 20 17:54:05 helena NetworkManager: <info>  Updating allowed wireless network lists. 
Sep 20 17:54:05 helena NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```

---

### Post by Ingo88 on 2008-10-04
Here's another syslog. This time I was browsing my webmail in Firefox:

```
Oct  4 12:17:01 helena /USR/SBIN/CRON[6462]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  4 12:18:55 helena gdm[5628]: WARNING: gdm_slave_xioerror_handler: Vakava X-virhe – :0 käynnistetään uudelleen 
Oct  4 12:18:58 helena kernel: [ 4827.121803] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct  4 12:18:58 helena kernel: [ 4827.122534] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Oct  4 12:18:58 helena kernel: [ 4827.122874] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Oct  4 12:19:17 helena pulseaudio[6651]: pid.c: Stale PID file, overwriting.
Oct  4 12:19:21 helena hcid[5563]: Default passkey agent (:1.45, /org/bluez/passkey) registered
Oct  4 12:19:21 helena hcid[5563]: Default authorization agent (:1.45, /org/bluez/auth) registered
Oct  4 12:19:27 helena NetworkManager: <info>  Updating allowed wireless network lists. 
Oct  4 12:19:27 helena NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```

---

### Post by Ingo88 on 2008-10-11
Again. This time the computer was completely idle. There wasn't even anyone in the room when it happened. I just was surprised by seeing the login screen when I walked past the screen.

syslog:
```
Oct 11 15:00:44 helena -- MARK --
Oct 11 15:17:01 helena /USR/SBIN/CRON[6570]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 11 15:27:50 helena gdm[5621]: WARNING: gdm_slave_xioerror_handler: Vakava X-virhe &#8211; :0 käynnistetään uudelleen 
Oct 11 15:27:52 helena kernel: [ 8902.366373] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct 11 15:27:52 helena kernel: [ 8902.367268] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Oct 11 15:27:52 helena kernel: [ 8902.367617] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Oct 11 15:40:44 helena -- MARK --
Oct 11 15:56:28 helena pulseaudio[6755]: pid.c: Stale PID file, overwriting.
Oct 11 15:56:49 helena hcid[5556]: Default passkey agent (:1.48, /org/bluez/passkey) registered
Oct 11 15:56:49 helena hcid[5556]: Default authorization agent (:1.48, /org/bluez/auth) registered
Oct 11 15:56:54 helena NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 11 15:56:54 helena NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```

thought I'd also post the contents of Xorg.0.log:
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux helena 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 11 15:27:51 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
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
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) Open APM successful
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0691 card 0000,0000 rev c4 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8598 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0686 card 1106,0000 rev 22 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 0000,0000 rev 10 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:07:4: chip 1106,3057 card 0000,0000 rev 30 class 06,00,00 hdr 00
(II) PCI: 00:07:5: chip 1106,3058 card 1106,4511 rev 20 class 04,01,00 hdr 00
(II) PCI: 00:0f:0: chip 127a,2014 card 122d,4055 rev 01 class 07,80,00 hdr 00
(II) PCI: 00:10:0: chip 10ec,8139 card 1429,d010 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5046 card 1002,0008 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS rev 0, Mem @ 0xdc000000/26, 0xe1000000/14, I/O @ 0x9000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdbffffff to 0xd7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[1] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[2] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[3] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[4] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[5] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[6] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[7] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[8] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[9] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[11] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[12] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[13] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[1] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[2] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[3] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[4] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[5] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[6] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[7] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[8] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[9] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[11] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[12] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[13] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[12] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[15] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[19] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched ati from file name ati.ids in autoconfig
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset ATI Rage 128 Pro GL PF (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[12] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[13] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[15] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[19] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[6] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[7] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[8] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[15] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[22] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) R128(0): PCI bus 1 card 0 func 0
(II) R128(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) R128(0): Depth 24, (==) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 Pro GL PF (AGP)" (ChipID = 0x5046)
(--) R128(0): Linear framebuffer at 0xdc000000
(--) R128(0): MMIO registers at 0xe1000000
(--) R128(0): VideoRAM: 32768 kByte (64-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(II) R128(0): Primary Display == Type 3
(WW) R128(0): Can't determine panel dimensions, and none specified.
	Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=40000; xclk=12000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 32768 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level 2
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read successfully
(II) R128(0): Manufacturer: SAM  Model: c8  Serial#: 1146302775
(II) R128(0): Year: 2004  Week: 44
(II) R128(0): EDID Version: 1.3
(II) R128(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) R128(0): Sync:  Separate  Composite
(II) R128(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) R128(0): Gamma: 2.20
(II) R128(0): DPMS capabilities: Off; RGB/Color Display
(II) R128(0): First detailed timing is preferred mode
(II) R128(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) R128(0): blueX: 0.143 blueY: 0.102   whiteX: 0.318 whiteY: 0.339
(II) R128(0): Supported VESA Video Modes:
(II) R128(0): 720x400@70Hz
(II) R128(0): 640x480@60Hz
(II) R128(0): 640x480@67Hz
(II) R128(0): 640x480@72Hz
(II) R128(0): 640x480@75Hz
(II) R128(0): 800x600@56Hz
(II) R128(0): 800x600@60Hz
(II) R128(0): 800x600@72Hz
(II) R128(0): 800x600@75Hz
(II) R128(0): 832x624@75Hz
(II) R128(0): 1024x768@60Hz
(II) R128(0): 1024x768@70Hz
(II) R128(0): 1024x768@75Hz
(II) R128(0): 1280x1024@75Hz
(II) R128(0): Manufacturer's mask: 0
(II) R128(0): Supported Future Video Modes:
(II) R128(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) R128(0): Supported additional Video Mode:
(II) R128(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) R128(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) R128(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) R128(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) R128(0): Monitor name: SyncMaster
(II) R128(0): Serial No: HSHXA05168
(II) R128(0): EDID (in hex):
(II) R128(0): 	00ffffffffffff004c2dc80037315344
(II) R128(0): 	2c0e01036c221b782a6f8ba25a4d9424
(II) R128(0): 	1a5156bfef0081800101010101010101
(II) R128(0): 	010101010101302a009851002a403070
(II) R128(0): 	1300520e1100001e000000fd00384b1e
(II) R128(0): 	510e000a202020202020000000fc0053
(II) R128(0): 	796e634d61737465720a2020000000ff
(II) R128(0): 	00485348584130353136380a202000f6
(II) R128(0): EDID vendor "SAM", prod id 200
(II) R128(0): Using EDID range info for horizontal sync
(II) R128(0): Using EDID range info for vertical refresh
(II) R128(0): Printing DDC gathered Modelines:
(II) R128(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) R128(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) R128(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) R128(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) R128(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) R128(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) R128(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) R128(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) R128(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) R128(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) R128(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) R128(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) R128(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) R128(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) R128(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) R128(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(==) R128(0): Write-combining range (0xdc000000,0x2000000)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) R128(0): I2C device "DDC:ddc2" removed.
(EE) R128(0): No DFP detected
(II) R128(0): Configured Monitor: Using hsync range of 30.00-81.00 kHz
(II) R128(0): Configured Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) R128(0): Configured Monitor: Using maximum pixel clock of 140.00 MHz
(II) R128(0): Estimated virtual size for aspect ratio 1.2593 is 1280x1024
(II) R128(0): Clock range:  12.50 to 400.00 MHz
(II) R128(0): Not using default mode "640x350" (vrefresh out of range)
(II) R128(0): Not using default mode "320x175" (vrefresh out of range)
(II) R128(0): Not using default mode "640x400" (vrefresh out of range)
(II) R128(0): Not using default mode "320x200" (vrefresh out of range)
(II) R128(0): Not using default mode "720x400" (vrefresh out of range)
(II) R128(0): Not using default mode "360x200" (vrefresh out of range)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(II) R128(0): Not using default mode "320x240" (vrefresh out of range)
(II) R128(0): Not using default mode "800x600" (vrefresh out of range)
(II) R128(0): Not using default mode "400x300" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of range)
(II) R128(0): Not using default mode "512x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1152x768" (vrefresh out of range)
(II) R128(0): Not using default mode "576x384" (vrefresh out of range)
(II) R128(0): Not using default mode "1152x864" (vrefresh out of range)
(II) R128(0): Not using default mode "576x432" (vrefresh out of range)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(II) R128(0): Not using default mode "1440x900" (width too large for virtual size)
(II) R128(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(II) R128(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(--) R128(0): Virtual size is 1280x1024 (pitch 1280)
(**) R128(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) R128(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) R128(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) R128(0): *Driver mode "1280x1024": 109.0 MHz, 63.7 kHz, 59.9 Hz
(II) R128(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(**) R128(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) R128(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) R128(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) R128(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(**) R128(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) R128(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) R128(0): *Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(**) R128(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) R128(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) R128(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) R128(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) R128(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) R128(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) R128(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) R128(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "960x600"x60.0   96.58  960 1024 1128 1296  600 600 602 621 doublescan (74.5 kHz)
(**) R128(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) R128(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) R128(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) R128(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) R128(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) R128(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) R128(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) R128(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) R128(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) R128(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) R128(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) R128(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) R128(0): *Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) R128(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
(**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
(**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "840x525"x60.1   73.57  840 892 984 1128  525 525 527 543 doublescan (65.2 kHz)
(**) R128(0): *Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) R128(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
(**) R128(0): *Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(II) R128(0): Modeline "700x525"x70.0   75.50  700 732 828 980  525 525 527 550 doublescan +hsync +vsync (77.0 kHz)
(**) R128(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) R128(0): *Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
(**) R128(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) R128(0): *Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) R128(0): Modeline "720x450"x60.2   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync (56.9 kHz)
(**) R128(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) R128(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) R128(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) R128(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) R128(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) R128(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) R128(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) R128(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) R128(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) R128(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) R128(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) R128(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) R128(0): *Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "640x400"x60.0   41.73  640 672 740 840  400 400 402 414 doublescan (49.7 kHz)
(**) R128(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) R128(0): *Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "640x384"x60.1   40.07  640 672 740 840  384 384 386 397 doublescan (47.7 kHz)
(**) R128(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) R128(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) R128(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) R128(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) R128(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) R128(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) R128(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) R128(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) R128(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
(**) R128(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) R128(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(**) R128(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) R128(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) R128(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) R128(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
(**) R128(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) R128(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
(**) R128(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) R128(0): Display dimensions: (340, 270) mm
(**) R128(0): DPI set to (95, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe1000000 - 0xe1003fff (0x4000) MS[B]
	[1] 0	0	0xdc000000 - 0xdfffffff (0x4000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe2010000 - 0xe20100ff (0x100) MX[B]
	[7] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B]
	[8] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[9] -1	0	0xe1000000 - 0xe1003fff (0x4000) MX[B](B)
	[10] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[14] 0	0	0x00009000 - 0x000090ff (0x100) IS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[21] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[23] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[25] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) R128(0): Write-combining range (0xdc000000,0x2000000)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
(II) R128(0): [drm] framebuffer handle = 0xdc000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(II) R128(0): [agp] Mode 0x1f000201 [AGP 0x1106/0x0691; Card 0x1002/0x5046]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II) R128(0): [agp] ring handle = 0xd8000000
(II) R128(0): [agp] Ring mapped at 0xb7a19000
(II) R128(0): [agp] ring read ptr handle = 0xd8101000
(II) R128(0): [agp] Ring read ptr mapped at 0xb7a18000
(II) R128(0): [agp] vertex/indirect buffers handle = 0xd8102000
(II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb5749000
(II) R128(0): [agp] AGP texture map handle = 0xd8302000
(II) R128(0): [agp] AGP Texture map mapped at 0xb5269000
(II) R128(0): [drm] register handle = 0xe1000000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (1280,4096)
(II) R128(0): Reserved area from (0,1024) to (1280,1026)
(II) R128(0): Largest offscreen area available: 1280 x 3070
(II) R128(0): Reserved back buffer from (0,1026) to (1280,2050)
(II) R128(0): Reserved depth buffer from (0,2050) to (1280,3075)
(II) R128(0): Reserved depth span from (0,3074) offset 0xf02800
(II) R128(0): Reserved 12288 kb for textures at offset 0x1400000
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		9 256x256 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 12300)
(II) R128(0): Largest offscreen area available: 1280 x 1019
(II) R128(0): DPMS enabled
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 10
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "fi"
(**) Generic Keyboard: XkbLayout: "fi"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
```

The system has also been weirdly slow lately. It's not even long ago I installed Hardy. Maybe sometime in August... It was 8.04.1 anyhow. I don't see why it's so slow either. Neither the CPU usage nor the memory usage seem high when the system feels awfully slow. Especially at startup (the gnome panel takes forever to load, and sometimes some applets fail to load). 

Could it be some bug with Xorg that's causing my troubles? Should I go to [bugs.launchpad.net]("https://bugs.launchpad.net/xorg/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=xorg") and look for help?

---

### Post by Ingo88 on 2008-10-14
I have now made a bug report: [https://bugs.launchpad.net/xserver-xorg-driver-vesa/+bug/283255](https://bugs.launchpad.net/xserver-xorg-driver-vesa/+bug/283255)

---

### Post by Ingo88 on 2008-12-15
Bump. I am soon going to give up...

---

### Post by Ingo88 on 2008-12-31
That's it. I give up. I'm giving Xubuntu a chance, but if that doesn't work either I guess I have no other choice but to go back to Windows...

---

### Post by Ingo88 on 2008-12-31
Xubuntu seemed to work fine (I installed it yesterday) until I tried to burn a CD using Brasero. During the burning process the same thing happened again. I'll install Windows 2000 tomorrow. Bye.

---

