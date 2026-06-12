---
title: "laptop built-in card reader problem"
date: 2009-03-01
forum: Hardware
---

### Post by Arq52 on 2009-03-01
Hi,
The internal SD card reader on my laptop ASUS U6VC doesn't work under intrepid 8.10 kernel  2.6.27-11.

After several search, I don't find any help.
Just that some others have the same problem with this "realtek" card reader
[http://www.uluga.ubuntuforums.org/showthread.php?p=6649680]("http://www.uluga.ubuntuforums.org/showthread.php?p=6649680")

So any help will be appreciated.

dmesg
```

[    7.036111] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    7.204652] usb 6-1: configuration #1 chosen from 1 choice
[    7.208011] scsi6 : SCSI emulation for USB Mass Storage devices
[    7.208207] usbcore: registered new interface driver usb-storage
[    7.208212] USB Mass Storage support registered.
[    7.208431] usb-storage: device found at 2
[    7.208434] usb-storage: waiting for device to settle before scanning
[   12.208854] usb-storage: device scan complete
[   12.215270] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   12.216672] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   12.216770] sd 6:0:0:0: Attached scsi generic sg2 type 0

```
sudo lsusb -d 0bda:0158 -v
```

Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x0158 Mass Stroage Device
  bcdDevice           51.95
  iManufacturer           1 Generic
  iProduct                2 USB2.0-CRW
  iSerial                 3 20060413092100000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 CARD READER
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 Bulk-In, Bulk-Out, Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```
sudo lshw -C disk
```

*-disk                  
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
  *-disk
       description: ATA Disk
       product: ST9320320AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0303
       serial: 5SX0L6HJ
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=cac5244c
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-U20N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HR05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```

---

### Post by Arq52 on 2009-03-07
up

---

### Post by ninboy on 2009-04-25
Second this... Exactly the same specs, and my card don't get recognized...

The difference is that in Ubuntu 8.10 it was working fine, in 9.04 no...

---

### Post by Arq52 on 2009-04-26
Now I am under ubuntu 9.04 and 2.6.28-11, but I have still the issue !

Edit : in fact it seems that my SD card was bad.
I made a test with a friend's card and it works !

---

### Post by nhudan on 2009-04-28
The same problem!
Asus U6EP

---

### Post by nhudan on 2009-07-04
anyone help us please!

---

### Post by ninboy on 2009-07-04
Fix released

sorry, I forgot about this thread... I published a "fix" in this launchpad bug.

[https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/367099](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/367099)

You should be able to use the card reader again :)

---

### Post by nhudan on 2009-07-05
Thanks for help!
i have done the same you said:
> In root shell (sudo -s), write and remount

echo "usb-storage" >> /etc/modules; modprobe usb-storage
but nothing happens ,and my SD has not recognized a card 
This is output of
sudo lsusb -d 0bda:0158 -v
```
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x0158 Mass Stroage Device
  bcdDevice           51.95
  iManufacturer           1 Generic
  iProduct                2 USB2.0-CRW
  iSerial                 3 20060413092100000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 CARD READER
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 Bulk-In, Bulk-Out, Interface
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
``` Thanks    and sorry about my stupid English!
Please help me detail

---

### Post by ninboy on 2009-07-05
> **nhudan said:**
> Thanks for help!
i have done the same you said:

What's your output of? ```
modprobe -lv | grep "usb-storage"
```

---

### Post by nhudan on 2009-07-05
d@d:~$ modprobe -lv | grep "usb-storage"
```
kernel/drivers/usb/storage/usb-storage.ko

```d@d:~$

---

### Post by ninboy on 2009-07-05
> **nhudan said:**
> d@d:~$ modprobe -lv | grep "usb-storage"
```
kernel/drivers/usb/storage/usb-storage.ko

```d@d:~$

Silly question, but have you tried removing and re-inserting the SD card?

And after doing that, what's your output of dmesg ?

---

### Post by nhudan on 2009-07-05
This is output of the dmesg ```

[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf7a0000 (usable)
[    0.000000]  BIOS-e820: 00000000bf7a0000 - 00000000bf7ae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf7ae000 - 00000000bf7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7f0000 - 00000000bf800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xbf7a0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf7a0000 (usable)
[    0.000000]  modified: 00000000bf7a0000 - 00000000bf7ae000 (ACPI data)
[    0.000000]  modified: 00000000bf7ae000 - 00000000bf7f0000 (ACPI NVS)
[    0.000000]  modified: 00000000bf7f0000 - 00000000bf800000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378c0000 - 37fefcd0
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb0cd0
[    0.000000] Move RAMDISK from 00000000378c0000 - 0000000037fefccf to 00881000 - 00fb0ccf
[    0.000000] ACPI: RSDP 000F81D0, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT BF7A0100, 0084 (r1 _ASUS_ Notebook  6000805 MSFT       97)
[    0.000000] ACPI: FACP BF7A0290, 00F4 (r3 A_M_I_ OEMFACP   6000805 MSFT       97)
[    0.000000] ACPI: DSDT BF7A0680, C3E0 (r1  U6S00 U6S00303      303 INTL 20051117)
[    0.000000] ACPI: FACS BF7AE000, 0040
[    0.000000] ACPI: APIC BF7A0390, 005C (r1 A_M_I_ OEMAPIC   6000805 MSFT       97)
[    0.000000] ACPI: MCFG BF7A0430, 003C (r1 A_M_I_ OEMMCFG   6000805 MSFT       97)
[    0.000000] ACPI: SLIC BF7A0470, 0176 (r1 _ASUS_ Notebook  6000805 MSFT       97)
[    0.000000] ACPI: DBGP BF7A03F0, 0034 (r1 A_M_I_ OEMDBGP   6000805 MSFT       97)
[    0.000000] ACPI: BOOT BF7A05F0, 0028 (r1 A_M_I_ OEMBOOT   6000805 MSFT       97)
[    0.000000] ACPI: ECDT BF7A0620, 0054 (r1 A_M_I_ OEMECDT   6000805 MSFT       97)
[    0.000000] ACPI: OEMB BF7AE040, 0060 (r1 A_M_I_ AMI_OEM   6000805 MSFT       97)
[    0.000000] ACPI: HPET BF7ACA60, 0038 (r1 A_M_I_ OEMHPET   6000805 MSFT       97)
[    0.000000] ACPI: GSCI BF7AE0A0, 2024 (r1 A_M_I_ GMCHSCI   6000805 MSFT       97)
[    0.000000] ACPI: ATKG BF7B02D0, 8024 (r1 A_M_I_  OEMATKG  5000702 MSFT       97)
[    0.000000] ACPI: SSDT BF7B8E50, 04E6 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2179MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb0cd0]      NEW RAMDISK ==> [0000881000 - 0000fb0cd0]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bf7a0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf7a0
[    0.000000] On node 0 totalpages: 784175
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4360 pages used for memmap
[    0.000000]   HighMem zone: 553626 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e3000
[    0.000000] PM: Registered nosave memory: 00000000000e3000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: bf800000:3f600000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 778047
[    0.000000] Kernel command line: root=UUID=af2ad229-81c3-4bf9-9f71-b35fe4257efd ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2393.782 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15685440 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3079988k/3137152k available (4126k kernel code, 55848k reserved, 2208k data, 532k init, 2231944k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.56 BogoMIPS (lpj=9575128)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018008] ACPI: Core revision 20080926
[    0.022069] ACPI: Checking initramfs for custom DSDT
[    0.280392] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.320084] CPU0: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz stepping 0b
[    0.324001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4787.95 BogoMIPS (lpj=9575907)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.408557] CPU1: Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz stepping 0b
[    0.408571] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.412033] Brought up 2 CPUs
[    0.412036] Total of 2 processors activated (9575.51 BogoMIPS).
[    0.412089] CPU0 attaching sched-domain:
[    0.412092]  domain 0: span 0-1 level MC
[    0.412093]   groups: 0 1
[    0.412099] CPU1 attaching sched-domain:
[    0.412100]  domain 0: span 0-1 level MC
[    0.412102]   groups: 1 0
[    0.412162] net_namespace: 776 bytes
[    0.412162] Booting paravirtualized kernel on bare hardware
[    0.412271] Time:  4:36:01  Date: 07/05/09
[    0.412271] regulator: core version 0.5
[    0.412271] NET: Registered protocol family 16
[    0.412271] EISA bus registered
[    0.412271] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.412271] ACPI: bus type pci registered
[    0.412271] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
[    0.412271] PCI: Not using MMCONFIG.
[    0.412394] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[    0.412395] PCI: Using configuration type 1 for base access
[    0.413288] ACPI: EC: EC description table is found, configuring boot EC
[    0.413101] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.429099] ACPI: Interpreter enabled
[    0.429105] ACPI: (supports S0 S1 S3 S4 S5)
[    0.429126] ACPI: Using IOAPIC for interrupt routing
[    0.430579] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
[    0.433736] PCI: MCFG area at c0000000 reserved in ACPI motherboard resources
[    0.433738] PCI: Using MMCONFIG for extended config space
[    0.441633] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.441634] ACPI: EC: driver started in interrupt mode
[    0.441854] ACPI: No dock devices found.
[    0.441937] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.442013] pci 0000:00:02.0: reg 10 64bit mmio: [0xfeb00000-0xfebfffff]
[    0.442020] pci 0000:00:02.0: reg 18 64bit mmio: [0xe0000000-0xefffffff]
[    0.442024] pci 0000:00:02.0: reg 20 io port: [0xec00-0xec07]
[    0.442054] pci 0000:00:02.1: reg 10 64bit mmio: [0xfe900000-0xfe9fffff]
[    0.442161] pci 0000:00:1a.0: reg 20 io port: [0xe000-0xe01f]
[    0.442223] pci 0000:00:1a.1: reg 20 io port: [0xdc00-0xdc1f]
[    0.442293] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfeaff400-0xfeaff7ff]
[    0.442341] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.442346] pci 0000:00:1a.7: PME# disabled
[    0.442401] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfeaf8000-0xfeafbfff]
[    0.442441] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.442445] pci 0000:00:1b.0: PME# disabled
[    0.442511] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.442516] pci 0000:00:1c.0: PME# disabled
[    0.442584] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.442589] pci 0000:00:1c.1: PME# disabled
[    0.442658] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.442662] pci 0000:00:1c.2: PME# disabled
[    0.442730] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.442734] pci 0000:00:1c.3: PME# disabled
[    0.442798] pci 0000:00:1d.0: reg 20 io port: [0xd880-0xd89f]
[    0.442860] pci 0000:00:1d.1: reg 20 io port: [0xd800-0xd81f]
[    0.442922] pci 0000:00:1d.2: reg 20 io port: [0xd480-0xd49f]
[    0.442989] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfeaff000-0xfeaff3ff]
[    0.443037] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.443042] pci 0000:00:1d.7: PME# disabled
[    0.443199] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.443203] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.443239] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.443246] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.443254] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.443262] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.443269] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.443340] pci 0000:00:1f.2: reg 10 io port: [0xe880-0xe887]
[    0.443347] pci 0000:00:1f.2: reg 14 io port: [0xe800-0xe803]
[    0.443355] pci 0000:00:1f.2: reg 18 io port: [0xe480-0xe487]
[    0.443362] pci 0000:00:1f.2: reg 1c io port: [0xe400-0xe403]
[    0.443370] pci 0000:00:1f.2: reg 20 io port: [0xe080-0xe09f]
[    0.443377] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfeaff800-0xfeafffff]
[    0.443397] pci 0000:00:1f.2: PME# supported from D3hot
[    0.443401] pci 0000:00:1f.2: PME# disabled
[    0.443548] pci 0000:00:1c.1: bridge io port: [0xb000-0xbfff]
[    0.443553] pci 0000:00:1c.1: bridge 32bit mmio: [0xfdd00000-0xfe4fffff]
[    0.443561] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xdbc00000-0xddbfffff]
[    0.443637] pci 0000:04:00.0: reg 10 io port: [0xc800-0xc8ff]
[    0.443667] pci 0000:04:00.0: reg 18 64bit mmio: [0xfe5ff000-0xfe5fffff]
[    0.443696] pci 0000:04:00.0: reg 30 32bit mmio: [0xfe5c0000-0xfe5dffff]
[    0.443711] pci 0000:04:00.0: supports D1 D2
[    0.443713] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.443719] pci 0000:04:00.0: PME# disabled
[    0.443790] pci 0000:00:1c.2: bridge io port: [0xc000-0xcfff]
[    0.443795] pci 0000:00:1c.2: bridge 32bit mmio: [0xfe500000-0xfe5fffff]
[    0.443918] pci 0000:05:00.0: reg 10 64bit mmio: [0xfe6fe000-0xfe6fffff]
[    0.444011] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
[    0.444031] pci 0000:05:00.0: PME# disabled
[    0.444121] pci 0000:00:1c.3: bridge 32bit mmio: [0xfe600000-0xfe6fffff]
[    0.444194] pci 0000:00:1e.0: transparent bridge
[    0.444238] bus 00 -> node 0
[    0.444246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.444523] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.444653] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.444797] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.444929] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.445060] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.462907] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    0.463070] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 12)
[    0.463230] ACPI: PCI Interrupt Link [LNKC] (IRQs *3)
[    0.463388] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *7 10 12)
[    0.463547] ACPI: PCI Interrupt Link [LNKE] (IRQs *6)
[    0.463706] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 12)
[    0.463866] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 12)
[    0.464036] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 12)
[    0.467561] ACPI Warning (tbutils-0217): Incorrect checksum in table [ATKG] - 76, should be 59 [20080926]
[    0.467586] ACPI: WMI: Mapper loaded
[    0.467616] SCSI subsystem initialized
[    0.467616] libata version 3.00 loaded.
[    0.467616] usbcore: registered new interface driver usbfs
[    0.467616] usbcore: registered new interface driver hub
[    0.467616] usbcore: registered new device driver usb
[    0.467616] PCI: Using ACPI for IRQ routing
[    0.472009] Bluetooth: Core ver 2.13
[    0.472019] NET: Registered protocol family 31
[    0.472019] Bluetooth: HCI device and connection manager initialized
[    0.472019] Bluetooth: HCI socket layer initialized
[    0.472019] NET: Registered protocol family 8
[    0.472019] NET: Registered protocol family 20
[    0.472026] NetLabel: Initializing
[    0.472028] NetLabel:  domain hash size = 128
[    0.472029] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.472039] NetLabel:  unlabeled traffic allowed by default
[    0.472052] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.472056] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.476046] AppArmor: AppArmor Filesystem Enabled
[    0.484007] pnp: PnP ACPI init
[    0.484013] ACPI: bus type pnp registered
[    0.486383] pnp: PnP ACPI: found 13 devices
[    0.486385] ACPI: ACPI bus type pnp unregistered
[    0.486388] PnPBIOS: Disabled by ACPI PNP
[    0.486396] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.486403] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.486405] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.486407] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.486409] system 00:08: ioport range 0x500-0x53f has been reserved
[    0.486412] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.486414] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.486416] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.486418] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.486420] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.486425] system 00:0a: ioport range 0x250-0x253 has been reserved
[    0.486427] system 00:0a: ioport range 0x256-0x25f has been reserved
[    0.486429] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.486431] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.486436] system 00:0b: iomem range 0xc0000000-0xcfffffff has been reserved
[    0.486441] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.486443] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.486445] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.486447] system 00:0c: iomem range 0x100000-0xbf7fffff could not be reserved
[    0.500607] Switched to high resolution mode on CPU 1
[    0.504006] Switched to high resolution mode on CPU 0
[    0.521131] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.521132] pci 0000:00:1c.0:   IO window: disabled
[    0.521138] pci 0000:00:1c.0:   MEM window: disabled
[    0.521142] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.521149] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.521152] pci 0000:00:1c.1:   IO window: 0xb000-0xbfff
[    0.521158] pci 0000:00:1c.1:   MEM window: 0xfdd00000-0xfe4fffff
[    0.521163] pci 0000:00:1c.1:   PREFETCH window: 0x000000dbc00000-0x000000ddbfffff
[    0.521171] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.521174] pci 0000:00:1c.2:   IO window: 0xc000-0xcfff
[    0.521180] pci 0000:00:1c.2:   MEM window: 0xfe500000-0xfe5fffff
[    0.521185] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.521192] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.521193] pci 0000:00:1c.3:   IO window: disabled
[    0.521199] pci 0000:00:1c.3:   MEM window: 0xfe600000-0xfe6fffff
[    0.521204] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.521211] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.521213] pci 0000:00:1e.0:   IO window: disabled
[    0.521218] pci 0000:00:1e.0:   MEM window: disabled
[    0.521222] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.521238] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.521243] pci 0000:00:1c.0: setting latency timer to 64
[    0.521252] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.521257] pci 0000:00:1c.1: setting latency timer to 64
[    0.521266] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.521271] pci 0000:00:1c.2: setting latency timer to 64
[    0.521280] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.521284] pci 0000:00:1c.3: setting latency timer to 64
[    0.521292] pci 0000:00:1e.0: setting latency timer to 64
[    0.521296] bus: 00 index 0 io port: [0x00-0xffff]
[    0.521298] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.521299] bus: 01 index 0 mmio: [0x0-0x0]
[    0.521301] bus: 01 index 1 mmio: [0x0-0x0]
[    0.521302] bus: 01 index 2 mmio: [0x0-0x0]
[    0.521303] bus: 01 index 3 mmio: [0x0-0x0]
[    0.521305] bus: 02 index 0 io port: [0xb000-0xbfff]
[    0.521307] bus: 02 index 1 mmio: [0xfdd00000-0xfe4fffff]
[    0.521308] bus: 02 index 2 mmio: [0xdbc00000-0xddbfffff]
[    0.521310] bus: 02 index 3 mmio: [0x0-0x0]
[    0.521311] bus: 04 index 0 io port: [0xc000-0xcfff]
[    0.521313] bus: 04 index 1 mmio: [0xfe500000-0xfe5fffff]
[    0.521314] bus: 04 index 2 mmio: [0x0-0x0]
[    0.521316] bus: 04 index 3 mmio: [0x0-0x0]
[    0.521317] bus: 05 index 0 mmio: [0x0-0x0]
[    0.521319] bus: 05 index 1 mmio: [0xfe600000-0xfe6fffff]
[    0.521320] bus: 05 index 2 mmio: [0x0-0x0]
[    0.521322] bus: 05 index 3 mmio: [0x0-0x0]
[    0.521323] bus: 06 index 0 mmio: [0x0-0x0]
[    0.521324] bus: 06 index 1 mmio: [0x0-0x0]
[    0.521326] bus: 06 index 2 mmio: [0x0-0x0]
[    0.521327] bus: 06 index 3 io port: [0x00-0xffff]
[    0.521329] bus: 06 index 4 mmio: [0x000000-0xffffffff]
[    0.521335] NET: Registered protocol family 2
[    0.536040] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.536231] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.536509] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.536648] TCP: Hash tables configured (established 131072 bind 65536)
[    0.536650] TCP reno registered
[    0.540051] NET: Registered protocol family 1
[    0.540141] checking if image is initramfs... it is
[    1.042374] Freeing initrd memory: 7359k freed
[    1.042410] Simple Boot Flag at 0x52 set to 0x1
[    1.042561] cpufreq: No nForce2 chipset.
[    1.042679] audit: initializing netlink socket (disabled)
[    1.042701] type=2000 audit(1246768561.041:1): initialized
[    1.048604] highmem bounce pool size: 64 pages
[    1.048609] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.049666] VFS: Disk quotas dquot_6.5.1
[    1.049713] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.050194] fuse init (API version 7.10)
[    1.050260] msgmni has been set to 1672
[    1.050399] alg: No test for stdrng (krng)
[    1.050408] io scheduler noop registered
[    1.050410] io scheduler anticipatory registered
[    1.050411] io scheduler deadline registered
[    1.050422] io scheduler cfq registered (default)
[    1.050432] pci 0000:00:02.0: Boot video device
[    1.072959] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.073020] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.073056] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.073071] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.073083] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.073092] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.073166] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.073215] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.073247] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    1.073263] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.073273] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.073282] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.073352] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.073400] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.073432] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    1.073448] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.073460] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.073470] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.073540] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.073587] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.073620] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    1.073635] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.073645] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.073654] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.073729] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.074150] pciehp 0000:00:1c.0:pcie02: HPC vendor_id 8086 device_id 283f ss_vid 0 ss_did 0
[    1.074188] pciehp 0000:00:1c.0:pcie02: service driver pciehp loaded
[    1.074585] pciehp 0000:00:1c.1:pcie02: HPC vendor_id 8086 device_id 2841 ss_vid 0 ss_did 0
[    1.074618] pciehp 0000:00:1c.1:pcie02: service driver pciehp loaded
[    1.075012] pciehp 0000:00:1c.2:pcie02: HPC vendor_id 8086 device_id 2843 ss_vid 0 ss_did 0
[    1.075044] pciehp 0000:00:1c.2:pcie02: service driver pciehp loaded
[    1.075442] pciehp 0000:00:1c.3:pcie02: HPC vendor_id 8086 device_id 2845 ss_vid 0 ss_did 0
[    1.075474] pciehp 0000:00:1c.3:pcie02: service driver pciehp loaded
[    1.075480] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.075643] ACPI: AC Adapter [AC0] (on-line)
[    1.107712] ACPI: Battery Slot [BAT0] (battery present)
[    1.107774] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.107776] ACPI: Power Button (FF) [PWRF]
[    1.107820] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.107829] ACPI: Sleep Button (CM) [SLPB]
[    1.107863] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.112048] ACPI: Lid Switch [LID]
[    1.112632] ACPI: SSDT BF7B83D0, 02C8 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    1.113093] ACPI: SSDT BF7B8730, 0712 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    1.114112] Monitor-Mwait will be used to enter C-1 state
[    1.114114] Monitor-Mwait will be used to enter C-2 state
[    1.114125] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.114145] processor ACPI_CPU:00: registered as cooling_device0
[    1.114148] ACPI: Processor [P001] (supports 8 throttling states)
[    1.114440] ACPI: SSDT BF7B8300, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    1.114856] ACPI: SSDT BF7B86A0, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    1.115989] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.116003] processor ACPI_CPU:01: registered as cooling_device1
[    1.116006] ACPI: Processor [P002] (supports 8 throttling states)
[    1.122698] thermal LNXTHERM:01: registered as thermal_zone0
[    1.123619] ACPI: Thermal Zone [THRM] (52 C)
[    1.123662] isapnp: Scanning for PnP cards...
[    1.477509] isapnp: No Plug & Play device found
[    1.488175] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.489042] brd: module loaded
[    1.489283] loop: module loaded
[    1.489344] Fixed MDIO Bus: probed
[    1.489348] PPP generic driver version 2.4.2
[    1.489390] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.489413] Driver 'sd' needs updating - please use bus_type methods
[    1.489420] Driver 'sr' needs updating - please use bus_type methods
[    1.489452] ahci 0000:00:1f.2: version 3.0
[    1.489465] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.489499] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    1.489566] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.489569] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ems 
[    1.489574] ahci 0000:00:1f.2: setting latency timer to 64
[    1.489803] scsi0 : ahci
[    1.489871] scsi1 : ahci
[    1.489917] scsi2 : ahci
[    1.490021] ata1: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff900 irq 2299
[    1.490024] ata2: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff980 irq 2299
[    1.490027] ata3: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaffa00 irq 2299
[    1.972016] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.973226] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.973311] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    1.973313] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.973937] ata1.00: ATA-8: ST9250827AS, 3.AAA, max UDMA/133
[    1.973939] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.975238] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.975325] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    1.975327] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.975975] ata1.00: configured for UDMA/133
[    2.308016] ata2: SATA link down (SStatus 0 SControl 300)
[    2.644015] ata3: SATA link down (SStatus 0 SControl 300)
[    2.660086] scsi 0:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    2.660161] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.660173] sd 0:0:0:0: [sda] Write Protect is off
[    2.660175] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.660195] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.660239] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.660250] sd 0:0:0:0: [sda] Write Protect is off
[    2.660252] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.660271] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.660273]  sda: sda1 sda2 < sda5 sda6 > sda3
[    2.715129] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.715158] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.715195] ata_piix 0000:00:1f.1: version 2.12
[    2.715201] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.715233] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.715297] scsi3 : ata_piix
[    2.715343] scsi4 : ata_piix
[    2.715900] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.715902] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.876411] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-U10N, 1.02, max UDMA/33
[    2.892327] ata4.00: configured for UDMA/33
[    2.893813] ata5: port disabled. ignoring.
[    2.896426] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-U10N  1.02 PQ: 0 ANSI: 5
[    2.904679] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.904681] Uniform CD-ROM driver Revision: 3.20
[    2.904746] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.904775] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.905272] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.905287] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.905299] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.905302] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.905345] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.909255] ehci_hcd 0000:00:1a.7: debug port 1
[    2.909261] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.909273] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfeaff400
[    2.924008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.924057] usb usb1: configuration #1 chosen from 1 choice
[    2.924078] hub 1-0:1.0: USB hub found
[    2.924085] hub 1-0:1.0: 4 ports detected
[    2.924171] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.924181] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.924184] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.924216] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.928119] ehci_hcd 0000:00:1d.7: debug port 1
[    2.928126] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.928137] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeaff000
[    2.944008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.944062] usb usb2: configuration #1 chosen from 1 choice
[    2.944082] hub 2-0:1.0: USB hub found
[    2.944087] hub 2-0:1.0: 6 ports detected
[    2.944161] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.944173] uhci_hcd: USB Universal Host Controller Interface driver
[    2.944192] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.944198] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.944201] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.944234] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.944265] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    2.944322] usb usb3: configuration #1 chosen from 1 choice
[    2.944341] hub 3-0:1.0: USB hub found
[    2.944347] hub 3-0:1.0: 2 ports detected
[    2.944420] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.944426] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.944429] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.944460] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.944491] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000dc00
[    2.944548] usb usb4: configuration #1 chosen from 1 choice
[    2.944569] hub 4-0:1.0: USB hub found
[    2.944574] hub 4-0:1.0: 2 ports detected
[    2.944642] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.944647] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.944650] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.944686] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.944710] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    2.944774] usb usb5: configuration #1 chosen from 1 choice
[    2.944793] hub 5-0:1.0: USB hub found
[    2.944798] hub 5-0:1.0: 2 ports detected
[    2.944867] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.944872] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.944875] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.944906] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.944940] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    2.944997] usb usb6: configuration #1 chosen from 1 choice
[    2.945016] hub 6-0:1.0: USB hub found
[    2.945021] hub 6-0:1.0: 2 ports detected
[    2.945087] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.945093] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.945096] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.945131] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.945155] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    2.945214] usb usb7: configuration #1 chosen from 1 choice
[    2.945233] hub 7-0:1.0: USB hub found
[    2.945238] hub 7-0:1.0: 2 ports detected
[    2.945332] usbcore: registered new interface driver libusual
[    2.945360] usbcore: registered new interface driver usbserial
[    2.945369] USB Serial support registered for generic
[    2.945381] usbcore: registered new interface driver usbserial_generic
[    2.945383] usbserial: USB Serial Driver core
[    2.945423] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    2.947708] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.948372] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.948376] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.948378] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.948380] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.948382] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.952029] mice: PS/2 mouse device common for all mice
[    2.968063] rtc_cmos 00:03: RTC can wake from S4
[    2.968088] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.968118] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.968163] device-mapper: uevent: version 1.0.3
[    2.968230] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.968284] device-mapper: multipath: version 1.0.5 loaded
[    2.968286] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.968341] EISA: Probing bus 0 at eisa.0
[    2.968376] EISA: Detected 0 cards.
[    2.968454] cpuidle: using governor ladder
[    2.968525] cpuidle: using governor menu
[    2.968912] TCP cubic registered
[    2.968988] NET: Registered protocol family 10
[    2.969316] lo: Disabled Privacy Extensions
[    2.969573] NET: Registered protocol family 17
[    2.969589] Bluetooth: L2CAP ver 2.11
[    2.969590] Bluetooth: L2CAP socket layer initialized
[    2.969592] Bluetooth: SCO (Voice Link) ver 0.6
[    2.969594] Bluetooth: SCO socket layer initialized
[    2.969621] Marking TSC unstable due to TSC halts in idle
[    2.969623] Bluetooth: RFCOMM socket layer initialized
[    2.969628] Bluetooth: RFCOMM TTY layer initialized
[    2.969630] Bluetooth: RFCOMM ver 1.10
[    2.970565] Using IPI No-Shortcut mode
[    2.970618] registered taskstats version 1
[    2.970715]   Magic number: 1:383:615
[    2.970799] rtc_cmos 00:03: setting system clock to 2009-07-05 04:36:03 UTC (1246768563)
[    2.970802] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.970804] EDD information not available.
[    2.971054] Freeing unused kernel memory: 532k freed
[    2.971177] Write protecting the kernel text: 4128k
[    2.971225] Write protecting the kernel read-only data: 1532k
[    3.000128] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.215702] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.215731] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.215761] r8169 0000:04:00.0: setting latency timer to 64
[    3.215972] r8169 0000:04:00.0: irq 2298 for MSI/MSI-X
[    3.216501] eth0: RTL8168b/8111b at 0xf7c94000, 00:1f:c6:dc:3c:f7, XID 38000000 IRQ 2298
[    3.237096] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    3.385926] usb 1-4: configuration #1 chosen from 1 choice
[    3.389900] Initializing USB Mass Storage driver...
[    3.400072] scsi5 : SCSI emulation for USB Mass Storage devices
[    3.409151] usbcore: registered new interface driver usb-storage
[    3.409154] USB Mass Storage support registered.
[    3.409213] usb-storage: device found at 2
[    3.409215] usb-storage: waiting for device to settle before scanning
[    3.612077] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    3.818981] PM: Starting manual resume from disk
[    3.818983] PM: Resume from partition 8:3
[    3.818985] PM: Checking hibernation image.
[    3.819141] PM: Resume from disk failed.
[    3.841090] EXT4-fs: barriers enabled
[    3.852542] usb 2-5: configuration #1 chosen from 1 choice
[    3.855806] kjournald2 starting.  Commit interval 5 seconds
[    3.855829] EXT4-fs: delayed allocation enabled
[    3.855831] EXT4-fs: file extents enabled
[    3.855912] EXT4-fs: mballoc enabled
[    3.855915] EXT4-fs: mounted filesystem with ordered data mode.
[    4.000072] Clocksource tsc unstable (delta = -152105920 ns)
[    4.204058] usb 6-2: new full speed USB device using uhci_hcd and address 2
[    4.369139] usb 6-2: configuration #1 chosen from 1 choice
[    4.608062] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    4.848367] usb 7-2: configuration #1 chosen from 1 choice
[    8.178150] udev: starting version 141
[    8.410016] usb-storage: device scan complete
[    8.416761] scsi 5:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    8.583431] iTCO_vendor_support: vendor-support=0
[    8.639643] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    8.639869] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[    8.639877] iTCO_wdt: No card detected
[    8.691730] cfg80211: Calling CRDA to update world regulatory domain
[    8.705759] Linux agpgart interface v0.103
[    8.753823] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    8.754706] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    8.757521] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    8.830440] cfg80211: World regulatory domain updated:
[    8.830442] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.830444] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.830446] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.830447] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.830449] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.830451] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.842931] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    8.907981] Bluetooth: Generic Bluetooth USB driver ver 0.3
[    8.908092] usbcore: registered new interface driver btusb
[    8.960774] acpi device:22: registered as cooling_device2
[    8.960925] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e/input/input6
[    8.964103] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    9.118285] asus-laptop: Asus Laptop Support version 0.42
[    9.123135] asus-laptop: BSTS called, 0x7f7f returned
[    9.123180] asus-laptop:   U6Ep model detected
[    9.123857] asus-laptop: Brightness ignored, must be controlled by ACPI video driver
[    9.123877] Registered led device: asus::mail
[    9.222504] Linux video capture interface: v2.00
[    9.313243] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.479249] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.501951] uvcvideo: Found UVC 1.00 device USB2.0 0.3M UVC WebCam (04f2:b036)
[    9.503462] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    9.506596] input: USB2.0 0.3M UVC WebCam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input7
[    9.506767] usbcore: registered new interface driver uvcvideo
[    9.506785] USB Video Class driver (SVN r263)
[    9.641320] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    9.641464] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[    9.641466] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[    9.641467] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[    9.667948] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.667950] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[    9.668076] iwlagn 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.668087] iwlagn 0000:05:00.0: setting latency timer to 64
[    9.668183] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[    9.711126] iwlagn: Tunable channels: 13 802.11bg, 19 802.11a channels
[    9.711203] iwlagn 0000:05:00.0: irq 2297 for MSI/MSI-X
[    9.714542] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.781732] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.781785] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.815415] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    9.990819] lp: driver loaded but no devices found
[   10.168867] Adding 265064k swap on /dev/sda3.  Priority:-1 extents:1 across:265064k
[   10.187579] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000
[   10.230015] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   10.698106] EXT4 FS on sda1, internal journal on sda1:8
[   11.930716] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   11.930771] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   12.338409] type=1505 audit(1246768572.865:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2321
[   12.373768] type=1505 audit(1246768572.902:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2325
[   12.373837] type=1505 audit(1246768572.902:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2325
[   12.373866] type=1505 audit(1246768572.902:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2325
[   12.373894] type=1505 audit(1246768572.902:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2325
[   12.468741] type=1505 audit(1246768572.994:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2332
[   12.468863] type=1505 audit(1246768572.994:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2332
[   12.490355] type=1505 audit(1246768573.018:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2336
[   12.605484] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   16.706295] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   16.706298] vboxdrv: Successfully done.
[   16.706299] vboxdrv: Found 2 processor cores.
[   16.706365] vboxdrv: fAsync=0 offMin=0x198 offMax=0x828
[   16.706402] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   16.706404] vboxdrv: Successfully loaded version 2.2.4 (interface 0x000a0009).
[   17.529278] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.529280] Bluetooth: BNEP filters: protocol multicast
[   17.547384] Bridge firewalling registered
[   19.981132] [drm] Initialized drm 1.1.0 20060810
[   20.222216] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.222220] pci 0000:00:02.0: setting latency timer to 64
[   20.222320] pci 0000:00:02.0: irq 2296 for MSI/MSI-X
[   20.222395] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   20.223444] [drm:i915_setparam] *ERROR* unknown parameter 4
[   22.470960] r8169: eth0: link up
[   22.470967] r8169: eth0: link up
[   22.471733] iwlagn 0000:05:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   22.820412] Registered led device: iwl-phy0:radio
[   22.820591] Registered led device: iwl-phy0:assoc
[   22.823430] Registered led device: iwl-phy0:RX
[   22.823454] Registered led device: iwl-phy0:TX
[   22.847786] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.265393] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   27.266340] input: Bluetooth Travel Mouse as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/bluetooth/hci0/hci0:42/input9
[   27.273629] generic-bluetooth 0005:046D:B002.0001: input,hidraw0: BLUETOOTH HID v48.09 Mouse [Bluetooth Travel Mouse] on 00:1F:C6:56:49:61
[   33.140088] eth0: no IPv6 routers present
[   82.763206] wlan0: authenticate with AP 00:14:78:52:4f:8c
[   82.765083] wlan0: authenticated
[   82.765086] wlan0: associate with AP 00:14:78:52:4f:8c
[   82.768188] wlan0: RX AssocResp from 00:14:78:52:4f:8c (capab=0x431 status=0 aid=1)
[   82.768190] wlan0: associated
[   82.788935] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   82.837048] wlan0: deauthenticated
[   83.837422] wlan0: direct probe to AP 00:14:78:52:4f:8c try 1
[   83.846219] wlan0 direct probe responded
[   83.846223] wlan0: authenticate with AP 00:14:78:52:4f:8c
[   83.848077] wlan0: authenticated
[   83.848081] wlan0: associate with AP 00:14:78:52:4f:8c
[   83.850877] wlan0: deauthenticated
[   84.848070] wlan0: direct probe to AP 00:14:78:52:4f:8c try 2
[   84.853190] wlan0 direct probe responded
[   84.853193] wlan0: authenticate with AP 00:14:78:52:4f:8c
[   84.855046] wlan0: authenticated
[   84.855049] wlan0: associate with AP 00:14:78:52:4f:8c
[   84.857252] wlan0: RX ReassocResp from 00:14:78:52:4f:8c (capab=0x431 status=0 aid=2)
[   84.857254] wlan0: associated
[   84.875001] phy0: failed to restore operational channel after scan
[   93.604207] wlan0: no IPv6 routers present
[  424.000204] CE: hpet increasing min_delta_ns to 15000 nsec
[15305.204463] input: Bluetooth Travel Mouse as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/bluetooth/hci0/hci0:42/input10
[15305.212467] generic-bluetooth 0005:046D:B002.0002: input,hidraw1: BLUETOOTH HID v48.09 Mouse [Bluetooth Travel Mouse] on 00:1F:C6:56:49:61
[15474.838100] device eth0 entered promiscuous mode
[15840.507092] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[16997.320414] tcpdump uses obsolete (PF_INET,SOCK_PACKET)
[17525.972986] device eth0 left promiscuous mode
[18171.385185] device eth0 entered promiscuous mode
[18210.529178] device eth0 left promiscuous mode
[18225.909084] wlan0: No ProbeResp from current AP 00:14:78:52:4f:8c - assume out of range
[18233.309110] device eth0 entered promiscuous mode
[18241.497035] iwlagn: index 0 not used in uCode key table.
[18515.337110] device eth0 left promiscuous mode
[18517.501091] device eth0 entered promiscuous mode
[18558.907160] device eth0 left promiscuous mode


```

---

