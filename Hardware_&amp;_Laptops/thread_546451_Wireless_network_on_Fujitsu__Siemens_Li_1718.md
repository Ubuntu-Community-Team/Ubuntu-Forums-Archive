---
title: "Wireless network on Fujitsu  Siemens Li 1718"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by roadrash on 2007-09-08
I am having problems getting the wireless networking operating using Ubuntu 7.04 on this laptop.  I have read many tutorials for the Atheros AR5007EG network interface used in this laptop and i believe I have got close to get it working but there is still something a bit wrong and i need help.  AT the moment it seems like the interface isn't being activated at startup.  Once I get this sorted i will post it as a tutorial for others.

I based what i did on a post i read at [http://ubuntuforums/showthread.php?p=3205543](http://ubuntuforums/showthread.php?p=3205543)

I downloaded ndiswrapper 1.47 from: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/)

I downloaded the 32 bit XP driver for the Atheros AR5007EG frorm here: [http://www.atheros.cz/](http://www.atheros.cz/) 

These are the steps I have done so far based on what I have read:-

> 1. Disable ath_pci

#sudo rmmod ath_pci

2. put that module in the blacklist of modprobe to avoid it loading on the startup:

#sudo nano /etc/modprobe.d/blacklist-common

3. add the following line at the end of the file

blacklist ath_pci

4. Remove madwifi

#cd /lib/modules/$(uname -r)
#sudo rm -rf net
#sudo rm -rf madwifi
#sudo rm -rf madwifi-ng

5. cd /to your directory of madwifi-version (if it exists), do the following:
sudo make clean (you can do this step again and again to make sure madwifi is removed completely)

6. Check for the existence of any of the following modules, wlan,  ath_hal,  ath_pci.

#lsmod

  and remove them by typing

#sudo rmmod (moduleName)

NOW REBOOT

7. Use the synaptic package manager & Install the package called "build-essential".

8. put ndiswrapper-1.47.tar.gz in folder /home/username/  (at least version 1.47 must be used)

#cd /home/username/

9. Extract archive & install

#sudo tar xvzf ndiswrapper-1.47.tar.gz
#cd /home/username/ndiswrapper-1.47/
#sudo make
#sudo make install

10. Install driver by first exracting  xp driver files into home folder then:

#sudo ndiswrapper -i net5211.inf
#sudo ndiswrapper -l
#sudo modprobe ndiswrapper

#dmesg (shows that the card installed)
#iwlist wlan0 scan  (will show all APs arround you)

#sudo ndiswrapper -m

11.REBOOT


here is the output from lsmod


> Module                  Size  Used by
usb_storage            72256  1 
libusual               17936  1 usb_storage
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  2 
cpufreq_userspace       5408  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
asus_acpi              17308  0 
container               5248  0 
battery                10756  0 
sbs                    15652  0 
button                  8720  0 
i2c_ec                  5888  1 sbs
video                  16388  0 
ac                      6020  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
ipv6                  268704  10 
ndiswrapper           194608  0 
nls_iso8859_1           5120  2 
nls_cp437               6784  2 
vfat                   14208  2 
fat                    53916  1 vfat
nls_utf8                3072  2 
ntfs                  107764  2 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
joydev                 10816  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
i2c_piix4               9740  0 
i2c_core               22784  2 i2c_ec,i2c_piix4
ati_agp                10124  0 
agpgart                35400  1 ati_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
pcspkr                  4224  0 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
psmouse                38920  0 
serio_raw               7940  0 
af_packet              23816  8 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  7 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ata_generic             9092  0 
sata_sil               12808  4 
libata                125720  2 ata_generic,sata_sil
atiixp                  7440  0 [permanent]
scsi_mod              142348  4 usb_storage,sg,sd_mod,libata
ohci_hcd               22532  0 
8139too                27648  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
usbcore               134280  6 usb_storage,libusual,ndiswrapper,ohci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability



here is the output from ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:16:D3:65:11:EE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:452 (452.0 b)  TX bytes:452 (452.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:E5:F9:F7  
          inet6 addr: fe80::2c0:a8ff:fee5:f9f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:92 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:c0000000-c0010000 

wlan0:ava Link encap:Ethernet  HWaddr 00:C0:A8:E5:F9:F7  
          inet addr:169.254.13.119  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Memory:c0000000-c0010000 



and the output from dmesg:

> [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009dc00 end: 000000000009dc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009dc00 size: 0000000000002400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000037da0000 end: 0000000037ea0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000037ea0000 size: 0000000000060000 end: 0000000037f00000 type: 4
[    0.000000] copy_e820_map() start: 0000000037f00000 size: 0000000000100000 end: 0000000038000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ea0000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 894MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7d80
[    0.000000] Entering add_active_range(0, 0, 229024) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229024
[    0.000000]   HighMem    229024 ->   229024
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   229024
[    0.000000] On node 0 totalpages: 229024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1757 pages used for memmap
[    0.000000]   Normal zone: 223171 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7bc0
[    0.000000] ACPI: RSDT (v001 FSC    PC       0x06040000  LTP 0x00000000) @ 0x37ea2436
[    0.000000] ACPI: FADT (v001 ATI    Bonefish 0x06040000 ATI  0x000f4240) @ 0x37ea7d1e
[    0.000000] ACPI: SLIC (v001 FSC    PC       0x06040000 FSC  0x00000001) @ 0x37ea7d92
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x37ea7f08
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x37ea7f66
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x37ea7fc4
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x37ea2472
[    0.000000] ACPI: DSDT (v001 WS     Y4B_____ 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:a8000000)
[    0.000000] Detected 1866.908 MHz processor.
[   22.980561] Built 1 zonelists.  Total pages: 227235
[   22.980569] Kernel command line: root=UUID=47a6e489-4f11-438e-b4af-6df0eb40f6df ro quiet splash
[   22.980900] mapped APIC to ffffd000 (fee00000)
[   22.980905] mapped IOAPIC to ffffc000 (fec00000)
[   22.980911] Enabling fast FPU save and restore... done.
[   22.980916] Enabling unmasked SIMD FPU exception support... done.
[   22.980934] Initializing CPU#0
[   22.981044] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   22.982387] Console: colour VGA+ 80x25
[   22.983394] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   22.984356] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.023520] Memory: 896824k/916096k available (1992k kernel code, 18700k reserved, 893k data, 328k init, 0k highmem)
[   23.023540] virtual kernel memory layout:
[   23.023542]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   23.023545]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.023548]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.023551]     lowmem  : 0xc0000000 - 0xf7ea0000   ( 894 MB)
[   23.023553]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   23.023556]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   23.023559]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   23.023566] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.100940] Calibrating delay using timer specific routine.. 3738.88 BogoMIPS (lpj=7477768)
[   23.101014] Security Framework v1.0.0 initialized
[   23.101026] SELinux:  Disabled at boot.
[   23.101057] Mount-cache hash table entries: 512
[   23.101286] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[   23.101301] monitor/mwait feature present.
[   23.101305] using mwait in idle threads.
[   23.101313] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.101318] CPU: L2 cache: 2048K
[   23.101324] CPU: Physical Processor ID: 0
[   23.101327] CPU: Processor Core ID: 0
[   23.101332] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[   23.101350] Compat vDSO mapped to ffffe000.
[   23.101357] Remapping vsyscall page to ffffe000
[   23.101379] Checking 'hlt' instruction... OK.
[   23.117115] SMP alternatives: switching to UP code
[   23.117767] Early unpacking initramfs... done
[   23.836899] ACPI: Core revision 20060707
[   23.855304] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   24.269877] CPU0: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
[   24.269912] SMP alternatives: switching to SMP code
[   24.270102] Booting processor 1/1 eip 3000
[   24.280806] Initializing CPU#1
[   24.359740] Calibrating delay using timer specific routine.. 3733.96 BogoMIPS (lpj=7467927)
[   24.359753] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[   24.359764] monitor/mwait feature present.
[   24.359770] CPU: L1 I cache: 32K, L1 D cache: 32K
[   24.359775] CPU: L2 cache: 2048K
[   24.359780] CPU: Physical Processor ID: 0
[   24.359783] CPU: Processor Core ID: 1
[   24.359786] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[   24.360639] CPU1: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
[   24.360681] Total of 2 processors activated (7472.84 BogoMIPS).
[   24.360875] ENABLING IO-APIC IRQs
[   24.361135] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   24.507610] checking TSC synchronization across 2 CPUs: passed.
[    0.003994] Brought up 2 CPUs
[    0.332141] migration_cost=131
[    0.332666] Booting paravirtualized kernel on bare hardware
[    0.332805] Time: 23:28:58  Date: 08/08/107
[    0.332863] NET: Registered protocol family 16
[    0.333019] EISA bus registered
[    0.333028] ACPI: bus type pci registered
[    0.351357] PCI: PCI BIOS revision 2.10 entry at 0xfd424, last bus=12
[    0.351362] PCI: Using configuration type 1
[    0.351366] Setting up standard PCI resources
[    0.357954] ACPI: Interpreter enabled
[    0.357960] ACPI: Using IOAPIC for interrupt routing
[    0.359120] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.359133] PCI: Probing PCI hardware (bus 00)
[    0.361737] Boot video device is 0000:01:05.0
[    0.362296] PCI: Transparent bridge - 0000:00:14.4
[    0.362366] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.366489] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.369689] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.370207] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.370722] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.371237] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.371798] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.372319] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.372831] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.373344] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.373856] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[    2.387230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    2.387853] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    2.388643] Linux Plug and Play Support v0.97 (c) Adam Belay
[    2.388659] pnp: PnP ACPI init
[    2.392943] pnp: PnP ACPI: found 10 devices
[    2.392951] PnPBIOS: Disabled by ACPI PNP
[    2.393037] PCI: Using ACPI for IRQ routing
[    2.393042] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    2.422434] NET: Registered protocol family 8
[    2.422439] NET: Registered protocol family 20
[    2.422848] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[    2.422855] pnp: 00:08: ioport range 0x1200-0x120f has been reserved
[    2.422861] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[    2.422867] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[    2.423434] PCI: Bridge: 0000:00:01.0
[    2.423440]   IO window: 9000-9fff
[    2.423448]   MEM window: c0100000-c01fffff
[    2.423455]   PREFETCH window: d0000000-dfffffff
[    2.423462] PCI: Bridge: 0000:00:04.0
[    2.423465]   IO window: disabled.
[    2.423472]   MEM window: c0000000-c00fffff
[    2.423478]   PREFETCH window: disabled.
[    2.423485] PCI: Bridge: 0000:00:14.4
[    2.423494]   IO window: a000-afff
[    2.423505]   MEM window: f0200000-f02fffff
[    2.423514]   PREFETCH window: f0300000-f03fffff
[    2.423548] PCI: Enabling device 0000:00:04.0 (0000 -> 0002)
[    2.423558] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    2.423623] NET: Registered protocol family 2
[    2.461732] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.461965] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.463454] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.464224] TCP: Hash tables configured (established 131072 bind 65536)
[    2.464229] TCP reno registered
[    2.477859] checking if image is initramfs... it is
[    3.901816] Freeing initrd memory: 7009k freed
[    3.903092] audit: initializing netlink socket (disabled)
[    3.903125] audit(1189294141.104:1): initialized
[    3.903464] VFS: Disk quotas dquot_6.5.1
[    3.903503] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.903604] io scheduler noop registered
[    3.903610] io scheduler anticipatory registered
[    3.903614] io scheduler deadline registered
[    3.903639] io scheduler cfq registered (default)
[    3.903980] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    3.904040] assign_interrupt_mode Found MSI capability
[    3.904046] Allocate Port Service[0000:00:04.0:pcie00]
[    3.904373] isapnp: Scanning for PnP cards...
[    4.261374] isapnp: No Plug & Play device found
[    4.310060] Real Time Clock Driver v1.12ac
[    4.310170] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    4.311424] mice: PS/2 mouse device common for all mice
[    4.312575] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    4.312880] input: Macintosh mouse button emulation as /class/input/input0
[    4.312955] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    4.312962] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.313394] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.313724] i8042.c: Detected active multiplexing controller, rev 1.1.
[    4.313819] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.313826] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    4.313832] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    4.313838] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    4.313843] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    4.313999] EISA: Probing bus 0 at eisa.0
[    4.314015] Cannot allocate resource for EISA slot 1
[    4.314059] Cannot allocate resource for EISA slot 8
[    4.314063] EISA: Detected 0 cards.
[    4.325834] input: AT Translated Set 2 keyboard as /class/input/input1
[    4.344226] TCP cubic registered
[    4.344245] NET: Registered protocol family 1
[    4.344289] Starting balanced_irq
[    4.344309] Using IPI No-Shortcut mode
[    4.344478] ACPI: (supports S0 S3 S4 S5)
[    4.344574]   Magic number: 7:984:503
[    4.345240] Freeing unused kernel memory: 328k freed
[    4.347858] Time: tsc clocksource has been installed.
[    5.738198] Capability LSM initialized
[    5.807625] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    5.808702] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    5.809122] ACPI: CPU0 (power states: C1[C1] C3[C3])
[    5.810040] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    5.810454] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    5.810892] ACPI: CPU1 (power states: C1[C1] C3[C3])
[    6.313270] ACPI: Thermal Zone [TZS0] (47 C)
[    6.315896] ACPI: Thermal Zone [TZS2] (43 C)
[    6.816272] usbcore: registered new interface driver usbfs
[    6.816314] usbcore: registered new interface driver hub
[    6.816360] usbcore: registered new device driver usb
[    6.818170] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[    6.818192] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    6.818398] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    6.818470] ehci_hcd 0000:00:13.2: irq 16, io mem 0xc0506000
[    6.818486] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.818634] usb usb1: configuration #1 chosen from 1 choice
[    6.818690] hub 1-0:1.0: USB hub found
[    6.818700] hub 1-0:1.0: 8 ports detected
[    6.927179] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    6.927232] 8139cp 0000:0a:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    6.927238] 8139cp 0000:0a:07.0: Try the "8139too" driver instead.
[    6.930084] 8139too Fast Ethernet driver 0.9.28
[    6.930164] ACPI: PCI Interrupt 0000:0a:07.0[A] -> GSI 23 (level, low) -> IRQ 17
[    6.930912] eth0: RealTek RTL8139 at 0xf8874000, 00:16:d3:65:11:ee, IRQ 17
[    6.930918] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.947352] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.947404] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[    6.947425] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    6.947470] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    6.947503] ohci_hcd 0000:00:13.0: irq 16, io mem 0xc0504000
[    7.001581] usb usb2: configuration #1 chosen from 1 choice
[    7.001635] hub 2-0:1.0: USB hub found
[    7.001659] hub 2-0:1.0: 4 ports detected
[    7.105433] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[    7.105464] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    7.105508] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    7.105541] ohci_hcd 0000:00:13.1: irq 16, io mem 0xc0505000
[    7.161366] usb usb3: configuration #1 chosen from 1 choice
[    7.161419] hub 3-0:1.0: USB hub found
[    7.161440] hub 3-0:1.0: 4 ports detected
[    7.278463] SCSI subsystem initialized
[    7.279217] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    7.279254] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[    7.279274] ATIIXP: chipset revision 128
[    7.279279] ATIIXP: not 100% native mode: will probe irqs later
[    7.279295]     ide0: BM-DMA at 0x8460-0x8467, BIOS settings: hda:DMA, hdb:pio
[    7.279319] ATIIXP: simplex device: DMA disabled
[    7.279323] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[    7.279332] Probing IDE interface ide0...
[    7.290252] libata version 2.20 loaded.
[    8.012840] hda: Optiarc DVD RW AD-7540A, ATAPI CD/DVD-ROM drive
[    9.328000] Time: acpi_pm clocksource has been installed.
[    9.708000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    9.708000] Probing IDE interface ide1...
[   10.272000] sata_sil 0000:00:12.0: version 2.2
[   10.272000] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[   10.272000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 19
[   10.272000] ata1: SATA max UDMA/100 cmd 0xf887a080 ctl 0xf887a08a bmdma 0xf887a000 irq 19
[   10.272000] ata2: SATA max UDMA/100 cmd 0xf887a0c0 ctl 0xf887a0ca bmdma 0xf887a008 irq 19
[   10.272000] scsi0 : sata_sil
[   10.740000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   11.060000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   11.060000] ata1.00: ATA-7: WDC WD1200BEVS-22RST0, 04.01G04, max UDMA/133
[   11.060000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   11.068000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   11.068000] ata1.00: configured for UDMA/100
[   11.068000] scsi1 : sata_sil
[   11.380000] ata2: SATA link down (SStatus 0 SControl 300)
[   11.380000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-2 04.0 PQ: 0 ANSI: 5
[   11.392000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   11.392000] Uniform CD-ROM driver Revision: 3.20
[   11.412000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   11.412000] sda: Write Protect is off
[   11.412000] sda: Mode Sense: 00 3a 00 00
[   11.412000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.412000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   11.412000] sda: Write Protect is off
[   11.412000] sda: Mode Sense: 00 3a 00 00
[   11.412000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.412000]  sda: sda1 sda2 sda3 sda4
[   11.464000] sd 0:0:0:0: Attached scsi disk sda
[   11.472000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   11.844000] kjournald starting.  Commit interval 5 seconds
[   11.844000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.292000] eth0: link down
[   22.584000] NET: Registered protocol family 17
[   23.160000] input: PC Speaker as /class/input/input2
[   23.184000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.188000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.340000] Linux agpgart interface v0.102 (c) Dave Jones
[   23.428000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   23.528000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000
[   23.564000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   23.948000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
[   24.156000] hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...
[   24.632000] fuse init (API version 7.8)
[   24.700000] lp: driver loaded but no devices found
[   24.972000] EXT3 FS on sda4, internal journal
[   25.976000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   26.080000] NTFS volume version 3.1.
[   26.132000] NTFS volume version 3.1.
[   30.736000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   30.816000] ndiswrapper: driver net5211 (,07/26/2007,5.3.0.67) loaded
[   30.816000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   30.816000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[   30.816000] ndiswrapper (ZwClose:2467): closing handle 0xf08ce1a8 not implemented
[   30.816000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   31.232000] ndiswrapper: using IRQ 18
[   31.736000] wlan0: ethernet device 00:c0:a8:e5:f9:f7 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   31.736000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   31.736000] usbcore: registered new interface driver ndiswrapper
[   66.272000] NET: Registered protocol family 10
[   66.272000] lo: Disabled Privacy Extensions
[   66.272000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   76.460000] wlan0: no IPv6 routers present
[   77.100000] No dock devices found.
[   77.128000] Using specific hotkey driver
[   77.200000] ibm_acpi: ec object not found
[   77.248000] ACPI: AC Adapter [ADP1] (on-line)
[   77.276000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   77.332000] input: Power Button (FF) as /class/input/input4
[   77.332000] ACPI: Power Button (FF) [PWRF]
[   77.336000] input: Lid Switch as /class/input/input5
[   77.336000] ACPI: Lid Switch [LID0]
[   77.364000] input: Sleep Button (CM) as /class/input/input6
[   77.364000] ACPI: Sleep Button (CM) [SLPB]
[   77.376000] input: Power Button (CM) as /class/input/input7
[   77.376000] ACPI: Power Button (CM) [PWRB]
[   77.612000] ACPI: Battery Slot [BAT0] (battery absent)
[   77.688000] pcc_acpi: loading...
[   83.064000] ppdev: user-space parallel port driver
[   83.692000] apm: BIOS not found.
[   83.884000] Bluetooth: Core ver 2.11
[   83.884000] NET: Registered protocol family 31
[   83.884000] Bluetooth: HCI device and connection manager initialized
[   83.884000] Bluetooth: HCI socket layer initialized
[   83.928000] Bluetooth: L2CAP ver 2.8
[   83.928000] Bluetooth: L2CAP socket layer initialized
[   84.056000] Bluetooth: RFCOMM socket layer initialized
[   84.056000] Bluetooth: RFCOMM TTY layer initialized
[   84.056000] Bluetooth: RFCOMM ver 1.8
[   86.620000] hda-intel: Invalid position buffer, using LPIB read method instead.
[  498.804000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  498.824000] ndiswrapper (iw_set_ap_address:650): setting AP mac address failed (00010003)
[  509.204000] wlan0: no IPv6 routers present
[  558.824000] ndiswrapper (iw_set_ap_address:650): setting AP mac address failed (00010003)
[  558.828000] ndiswrapper (iw_set_ap_address:650): setting AP mac address failed (00010003)
[  598.156000] wlan0: no IPv6 routers present
[ 4153.612000] usb 1-2: new high speed USB device using ehci_hcd and address 2
[ 4153.744000] usb 1-2: configuration #1 chosen from 1 choice
[ 4154.132000] usbcore: registered new interface driver libusual
[ 4154.152000] Initializing USB Mass Storage driver...
[ 4154.152000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 4154.152000] usbcore: registered new interface driver usb-storage
[ 4154.152000] USB Mass Storage support registered.
[ 4154.152000] usb-storage: device found at 2
[ 4154.152000] usb-storage: waiting for device to settle before scanning
[ 4159.152000] usb-storage: device scan complete
[ 4159.152000] scsi 2:0:0:0: Direct-Access     Ut163    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[ 4159.152000] SCSI device sdb: 2015231 512-byte hdwr sectors (1032 MB)
[ 4159.156000] sdb: Write Protect is off
[ 4159.156000] sdb: Mode Sense: 00 00 00 00
[ 4159.156000] sdb: assuming drive cache: write through
[ 4159.156000] SCSI device sdb: 2015231 512-byte hdwr sectors (1032 MB)
[ 4159.160000] sdb: Write Protect is off
[ 4159.160000] sdb: Mode Sense: 00 00 00 00
[ 4159.160000] sdb: assuming drive cache: write through
[ 4159.160000]  sdb: sdb1
[ 4159.264000] sd 2:0:0:0: Attached scsi removable disk sdb
[ 4159.264000] sd 2:0:0:0: Attached scsi generic sg1 type 0


---

### Post by jay_b987 on 2007-10-20
dude i'm brand new to ubuntu (tonight actually) so have no clue what i'm doing there- same problem myself.

Based on what I can see though- theres absolutely nothing wrong with your initial driver setup at all.
I've got exactly the same setup (same problem)

Ubuntu picks up the wireless card AR5007EG fine and it is mentioned in the hardware thingy as on.

Exactly the same as when you go to configure a network from the terminal (execpt there's none to be found)

The problem is not with the wireless card itself, but activating the device via the hotkey. If you've got the same setup as me (1718), in windows, you have to hit the hotkey above the keyboard to activate the wireless card. If you don't (in windows) the device still appears as instaled and enabled in device manager, it just cant pick up any networks. My guess is the same is happening in Ubuntu.

The hotkey to activate the wireless runs off a driver(s) that comes from the 'launch_1718' (somethine like that) installation (in your c:\driver\soft folder). What I think we've got to do is find a linux driver for the hotkey, or find some way of bypassing it (which i think is impossible as I think its merely a swith) 

The problem is NDIS won't work on the one provided with the laptop (in the driver folder) as it is simply an install file and there's no '.inf' file in there. whether it needs that I don't know, i'm completely new to all this.

You seem like you've got a bit more idea as to whats going on in Ubuntu / Linux. I have no idea, so if this theory helps you. gimme a shout so I can get mine working too.

Cheers dude

---

### Post by Noir8 on 2007-10-21
Hi,
I hav a Li1718 and I've got Wlan working.
In Addition to the ndiwswrapper-module I downloaded acer_acpi
(Please google for the Url I don't have it available)
compiled the module modprobe acer_acpi
and then issued following command as root:
echo 1 > /proc/acpi/acer/wireless
The wlan-LED should turns on now and you should have a functioning and working wlan.
By
Noir8

---

### Post by John Mandrake on 2007-10-30
> **Noir8 said:**
> Hi,
I hav a Li1718 and I've got Wlan working.
In Addition to the ndiwswrapper-module I downloaded acer_acpi
(Please google for the Url I don't have it available)
compiled the module modprobe acer_acpi
and then issued following command as root:
echo 1 > /proc/acpi/acer/wireless
The wlan-LED should turns on now and you should have a functioning and working wlan.
By
Noir8

... and you did this on a Fujitsu/Amilo? ... with acer_acpi... I have a bad fealing about this!

---

### Post by gabi10 on 2007-11-18
it's incredible......it's the solution

thanks

 bye

---

### Post by damianusthesage on 2008-02-01
I just went into the directory where I've unpacked acer_acpi, on typing 

*./configure *

I get 

*bash: ./configure: No such file or directory*

when i try just to make, i get nothing, it just hangs. I guess I would see some output in the terminal if anything was hapening. this is so frustrating, I have the wlan0 working now, but not the special buttons.


any ideas?

---

### Post by roadrash on 2008-02-05
All the info above in this post is now out of date as there is now an offical native driver for the atheros AR5007EG chipset in MadWiFI drivers.   Go here for instructions on how to install .


[http://ubuntuforums.org/showthread.php?t=683919]("http://ubuntuforums.org/showthread.php?t=683919")

---

### Post by Daelyn on 2008-02-06
If I'm not totally wrong, there is some issue with MAC adresses and Atheros cards. Your dmesg output said "[ 558.824000] ndiswrapper (iw_set_ap_address:650): setting AP mac address failed (00010003)"

Read something about "soft mac" around the forum.

But, I guess, with the new driver this is out of topic.

best of luck.

---

