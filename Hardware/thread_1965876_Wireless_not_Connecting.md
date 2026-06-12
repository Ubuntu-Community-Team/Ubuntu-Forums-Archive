---
title: "Wireless not Connecting"
date: 2012-04-26
forum: Hardware
---

### Post by dalexnagy on 2012-04-26
I have a multi-boot Dell Inspiron 6400 laptop that is unable to connect via WiFi when booted under Ubuntu 10.04 but connects fine in Win7 (how this is being posted).  The WiFi LED is lit meaning it is enabled.  I have taken WiFi down (by hardware and by software) and re-enabled it but without success.

Details of the Intel wireless card are contained in the command outputs below.

This Linux is my normal and preferred OS and in my home office, I use a wired connection but due to work on our house, I am forced to use the wireless connection.  I have searched many sites and found many varied suggestions but none has worked for me.

If I have missed including any info, please ask and I will provide it.

If anyone can offer a suggestion that will get my wireless working, I will certainly appreciate it.

Thanks,
Dave

_**Basic Info:**_

When booted in Linux, the wireless shows as 'disconnected' yet some of the commands show that it has seen or is seeing my home wireless access point.  A wired connection works fine.

Here are the outputs from various commands as suggested by various support sites:

**_uname:_**

Linux davesdell 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:08:43 UTC 2012 i686 GNU/Linux


**_nm-tool:_**


NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:13:02:B8:65:19

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NagyFamily_NetGear: Infra, 00:22:3F:96:0B:AD, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:15:C5:25:F4:7A

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


**_iwconfig:_**

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
**_rfkill:_**

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

_**iwlist scan:**_

wlan0     Scan completed :
          Cell 01 - Address: 00:22:3F:96:0B:AD
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"NagyFamily_NetGear"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000040824dd
                    Extra: Last beacon: 1636ms ago
                    IE: Unknown: 00124E61677946616D696C795F4E657447656172
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1601001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000D4E6574676561722C20496E632E10230007574E523230303010240007574E523230303010420004353637381054000800060050F204000110110007574E5232303030100800020084103C000103

**_lsmod:_**

iwl3945                68727  0 
iwlcore               106149  1 iwl3945
mac80211              205434  2 iwl3945,iwlcore
led_class               2864  3 iwl3945,iwlcore,sdhci
cfg80211              126528  3 iwl3945,iwlcore,mac80211

_**cat /var/log/syslog (grep for 'iwl', 'firmware', 'wlan', 'wpa', & 'etwork'):**_

Apr 26 10:46:26 davesdell kernel: [   25.744605] Registered led device: iwl-phy0::RX
Apr 26 10:46:26 davesdell kernel: [   25.744857] Registered led device: iwl-phy0::TX
Apr 26 10:46:26 davesdell NetworkManager: <info>  (wlan0): preparing device.
Apr 26 10:46:26 davesdell NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Apr 26 10:46:26 davesdell NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Apr 26 10:46:26 davesdell NetworkManager: <info>  (eth0): carrier is OFF
Apr 26 10:46:26 davesdell NetworkManager: <info>  (eth0): new Ethernet device (driver: 'b44')
Apr 26 10:46:26 davesdell NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 26 10:46:26 davesdell NetworkManager: <info>  (eth0): now managed
Apr 26 10:46:26 davesdell NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Apr 26 10:46:26 davesdell NetworkManager: <info>  (eth0): bringing up device.
Apr 26 10:46:26 davesdell kernel: [   25.757064] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 26 10:46:26 davesdell NetworkManager: <info>  (eth0): preparing device.
Apr 26 10:46:26 davesdell NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Apr 26 10:46:26 davesdell avahi-daemon[878]: Network interface enumeration completed.
Apr 26 10:46:26 davesdell NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr 26 10:46:26 davesdell NetworkManager: <info>  modem-manager is now available
Apr 26 10:46:26 davesdell NetworkManager: <info>  Trying to start the supplicant...
Apr 26 10:46:26 davesdell NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Apr 26 10:46:26 davesdell NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Apr 26 10:46:26 davesdell NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Apr 26 10:46:28 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:46:29 davesdell snort[1384]: Initializing Network Interface eth0
Apr 26 10:46:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:47:16 davesdell dhclient: Listening on LPF/wlan0/00:13:02:b8:65:19
Apr 26 10:47:16 davesdell dhclient: Sending on   LPF/wlan0/00:13:02:b8:65:19
Apr 26 10:47:18 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:47:58 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:48:16 davesdell dhclient: Listening on LPF/wlan0/00:13:02:b8:65:19
Apr 26 10:48:16 davesdell dhclient: Sending on   LPF/wlan0/00:13:02:b8:65:19
Apr 26 10:48:23 davesdell kernel: [  142.248732] Registered led device: iwl-phy0::radio
Apr 26 10:48:23 davesdell kernel: [  142.248761] Registered led device: iwl-phy0::assoc
Apr 26 10:48:23 davesdell kernel: [  142.248786] Registered led device: iwl-phy0::RX
Apr 26 10:48:23 davesdell kernel: [  142.248810] Registered led device: iwl-phy0::TX
Apr 26 10:48:23 davesdell kernel: [  142.269263] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 26 10:48:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:49:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:50:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:51:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:52:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:53:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:54:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:55:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:56:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:57:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:58:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 10:59:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 11:00:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 11:01:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 11:02:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 11:03:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 11:04:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 11:05:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 11:06:48 davesdell wpa_supplicant[1001]: WPS-AP-AVAILABLE 
Apr 26 11:07:57 davesdell wpa_supplicant[1001]: last message repeated 2 times

[U][B]lshw - class network:
[/B][/U]
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:b8:65:19
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:26 memory:efdff000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:25:f4:7a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff

_**lsusb:**_

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


_**lspci:**_

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


_**dmesg:**_

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-41-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #88-Ubuntu SMP Thu Mar 29 13:08:43 UTC 2012 (Ubuntu 2.6.32-41.88-generic 2.6.32.59+drm33.24)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d3400 (usable)
[    0.000000]  BIOS-e820: 000000007f6d3400 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7f6d3 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F800000 mask FFF800000 uncachable
[    0.000000]   2 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f6d3400 (usable)
[    0.000000]  modified: 000000007f6d3400 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  modified: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 3784f000 - 37fef316
[    0.000000] Allocated new RAMDISK: 008ea000 - 0108a316
[    0.000000] Move RAMDISK from 000000003784f000 - 0000000037fef315 to 008ea000 - 0108a315
[    0.000000] ACPI: RSDP 000fc1d0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 7f6d39cd 00040 (v01 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: FACP 7f6d4800 00074 (v01 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: DSDT 7f6d5400 04766 (v01 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 7f6e3c00 00040
[    0.000000] ACPI: HPET 7f6d4f00 00038 (v01 DELL    M07     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 7f6d5000 00068 (v01 DELL    M07     27D60C12 ASL  00000047)
[    0.000000] ACPI: MCFG 7f6d4fc0 0003E (v16 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: SLIC 7f6d509c 00176 (v01 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: BOOT 7f6d4bc0 00028 (v01 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: SSDT 7f6d3a0d 004DC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e5f18]    TEXT DATA BSS ==> [0000100000 - 00008e5f18]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008e6000 - 00008e9188]              BRK ==> [00008e6000 - 00008e9188]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ea000 - 000108a316]      NEW RAMDISK ==> [00008ea000 - 000108a316]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f6d3
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f6d3
[    0.000000] On node 0 totalpages: 521838
[    0.000000] free_area_init_node: node 0, pgdat c07a0a20, node_mem_map c108c000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292311 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:70000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517760
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-41-generic root=UUID=6cf6b194-09ab-42b4-bfa6-3ffea1249e3f ro splash quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10438780 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f6d3)
[    0.000000] Memory: 2042852k/2087756k available (4698k kernel code, 43412k reserved, 2129k data, 664k init, 1178452k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07ab000 - 0xc0851000   ( 664 kB)
[    0.000000]       .data : 0xc0596ae7 - 0xc07aafc8   (2129 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0596ae7   (4698 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.479 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.95 BogoMIPS (lpj=6385916)
[    0.004028] Security Framework initialized
[    0.004056] AppArmor: AppArmor initialized
[    0.004067] Mount-cache hash table entries: 512
[    0.004232] Initializing cgroup subsys ns
[    0.004237] Initializing cgroup subsys cpuacct
[    0.004242] Initializing cgroup subsys memory
[    0.004251] Initializing cgroup subsys devices
[    0.004255] Initializing cgroup subsys freezer
[    0.004258] Initializing cgroup subsys net_cls
[    0.004285] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004289] CPU: L2 cache: 2048K
[    0.004294] CPU: Physical Processor ID: 0
[    0.004296] CPU: Processor Core ID: 0
[    0.004301] mce: CPU supports 6 MCE banks
[    0.004314] CPU0: Thermal monitoring enabled (TM2)
[    0.004319] using mwait in idle threads.
[    0.004328] Performance Events: no PMU driver, software events only.
[    0.004336] Checking 'hlt' instruction... OK.
[    0.024050] ACPI: Core revision 20090903
[    0.033293] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.033300] ftrace: allocating 21839 entries in 43 pages
[    0.036081] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036475] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078467] CPU0: Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 2048K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.164063] CPU1: Genuine Intel(R) CPU           T2050  @ 1.60GHz stepping 08
[    0.164075] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.168001] Measured 3281292372 cycles TSC warp between CPUs, turning off TSC clock.
[    0.168001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.168025] Brought up 2 CPUs
[    0.168029] Total of 2 processors activated (6385.84 BogoMIPS).
[    0.169121] CPU0 attaching sched-domain:
[    0.169127]  domain 0: span 0-1 level MC
[    0.169131]   groups: 0 1
[    0.169138] CPU1 attaching sched-domain:
[    0.169141]  domain 0: span 0-1 level MC
[    0.169145]   groups: 1 0
[    0.169228] devtmpfs: initialized
[    0.169228] regulator: core version 0.5
[    0.169228] Time: 10:46:01  Date: 04/26/12
[    0.169228] NET: Registered protocol family 16
[    0.169228] Trying to unpack rootfs image as initramfs...
[    0.169228] EISA bus registered
[    0.169228] ACPI: bus type pci registered
[    0.169228] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.169228] PCI: MCFG area at f0000000 reserved in E820
[    0.169228] PCI: Using MMCONFIG for extended config space
[    0.169228] PCI: Using configuration type 1 for base access
[    0.176497] bio: create slab <bio-0> at 0
[    0.177092] ACPI: EC: Look up EC in DSDT
[    0.194606] ACPI: Interpreter enabled
[    0.194614] ACPI: (supports S0 S3 S4 S5)
[    0.194642] ACPI: Using IOAPIC for interrupt routing
[    0.228581] ACPI: No dock devices found.
[    0.243651] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.243806] pci 0000:00:02.0: reg 10 32bit mmio: [0xeff00000-0xeff7ffff]
[    0.243814] pci 0000:00:02.0: reg 14 io port: [0xeff8-0xefff]
[    0.243821] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.243827] pci 0000:00:02.0: reg 1c 32bit mmio: [0xefec0000-0xefefffff]
[    0.243888] pci 0000:00:02.1: reg 10 32bit mmio: [0xeff80000-0xefffffff]
[    0.244041] pci 0000:00:1b.0: reg 10 64bit mmio: [0xefebc000-0xefebffff]
[    0.244139] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.244145] pci 0000:00:1b.0: PME# disabled
[    0.244282] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.244289] pci 0000:00:1c.0: PME# disabled
[    0.244433] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.244439] pci 0000:00:1c.3: PME# disabled
[    0.244517] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.244594] pci 0000:00:1d.1: reg 20 io port: [0xbf60-0xbf7f]
[    0.244672] pci 0000:00:1d.2: reg 20 io port: [0xbf40-0xbf5f]
[    0.244750] pci 0000:00:1d.3: reg 20 io port: [0xbf20-0xbf3f]
[    0.244832] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80000-0xffa803ff]
[    0.244926] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.244934] pci 0000:00:1d.7: PME# disabled
[    0.245150] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.245158] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.245165] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.245172] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.245267] pci 0000:00:1f.2: reg 10 io port: [0x1f0-0x1f7]
[    0.245277] pci 0000:00:1f.2: reg 14 io port: [0x3f4-0x3f7]
[    0.245287] pci 0000:00:1f.2: reg 18 io port: [0x170-0x177]
[    0.245297] pci 0000:00:1f.2: reg 1c io port: [0x374-0x377]
[    0.245307] pci 0000:00:1f.2: reg 20 io port: [0xbfa0-0xbfaf]
[    0.245361] pci 0000:00:1f.2: PME# supported from D3hot
[    0.245367] pci 0000:00:1f.2: PME# disabled
[    0.245443] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.245679] pci 0000:0b:00.0: reg 10 32bit mmio: [0xefdff000-0xefdfffff]
[    0.246019] pci 0000:0b:00.0: PME# supported from D0 D3hot D3cold
[    0.246033] pci 0000:0b:00.0: PME# disabled
[    0.246161] pci 0000:00:1c.0: bridge 32bit mmio: [0xefd00000-0xefdfffff]
[    0.246236] pci 0000:00:1c.3: bridge io port: [0xd000-0xdfff]
[    0.246243] pci 0000:00:1c.3: bridge 32bit mmio: [0xefa00000-0xefcfffff]
[    0.246253] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xe0000000-0xe01fffff]
[    0.246302] pci 0000:03:00.0: reg 10 32bit mmio: [0xef9fe000-0xef9fffff]
[    0.246381] pci 0000:03:00.0: supports D1 D2
[    0.246385] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.246391] pci 0000:03:00.0: PME# disabled
[    0.246441] pci 0000:03:01.0: reg 10 32bit mmio: [0xef9fd800-0xef9fdfff]
[    0.246524] pci 0000:03:01.0: supports D1 D2
[    0.246527] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.246533] pci 0000:03:01.0: PME# disabled
[    0.246584] pci 0000:03:01.1: reg 10 32bit mmio: [0xef9fd500-0xef9fd5ff]
[    0.246667] pci 0000:03:01.1: supports D1 D2
[    0.246670] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.246676] pci 0000:03:01.1: PME# disabled
[    0.246726] pci 0000:03:01.2: reg 10 32bit mmio: [0xef9fd600-0xef9fd6ff]
[    0.246812] pci 0000:03:01.2: supports D1 D2
[    0.246815] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.246822] pci 0000:03:01.2: PME# disabled
[    0.246872] pci 0000:03:01.3: reg 10 32bit mmio: [0xef9fd700-0xef9fd7ff]
[    0.246954] pci 0000:03:01.3: supports D1 D2
[    0.246957] pci 0000:03:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.246964] pci 0000:03:01.3: PME# disabled
[    0.247042] pci 0000:00:1e.0: transparent bridge
[    0.247052] pci 0000:00:1e.0: bridge 32bit mmio: [0xef900000-0xef9fffff]
[    0.247084] pci_bus 0000:00: on NUMA node 0
[    0.247095] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.247501] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.247613] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.247724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.260643] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.260800] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
[    0.260956] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.261108] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.261261] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.261421] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.261577] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.261734] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.261903] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.261922] vgaarb: loaded
[    0.262090] SCSI subsystem initialized
[    0.262216] libata version 3.00 loaded.
[    0.262314] usbcore: registered new interface driver usbfs
[    0.262332] usbcore: registered new interface driver hub
[    0.262433] usbcore: registered new device driver usb
[    0.262591] ACPI: WMI: Mapper loaded
[    0.262594] PCI: Using ACPI for IRQ routing
[    0.262872] NetLabel: Initializing
[    0.262875] NetLabel:  domain hash size = 128
[    0.262878] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.262896] NetLabel:  unlabeled traffic allowed by default
[    0.262941] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.262950] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.262957] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.272042] Switching to clocksource hpet
[    0.274806] AppArmor: AppArmor Filesystem Enabled
[    0.274829] pnp: PnP ACPI init
[    0.274852] ACPI: bus type pnp registered
[    0.311307] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.311313] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.311416] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.311421] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.311426] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.311431] pnp 00:03: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.312784] pnp: PnP ACPI: found 12 devices
[    0.312787] ACPI: ACPI bus type pnp unregistered
[    0.312792] PnPBIOS: Disabled by ACPI PNP
[    0.312811] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.312816] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.312820] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.312825] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.312829] system 00:00: iomem range 0x100000-0x7f6d33ff could not be reserved
[    0.312833] system 00:00: iomem range 0x7f6d3400-0x7f6fffff has been reserved
[    0.312837] system 00:00: iomem range 0x7f700000-0x7f7fffff has been reserved
[    0.312842] system 00:00: iomem range 0x7f700000-0x7fefffff could not be reserved
[    0.312846] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.312850] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.312855] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.312859] system 00:00: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.312863] system 00:00: iomem range 0xffa80000-0xffa83fff could not be reserved
[    0.312868] system 00:00: iomem range 0xf4000000-0xf4003fff has been reserved
[    0.312872] system 00:00: iomem range 0xf4004000-0xf4004fff has been reserved
[    0.312876] system 00:00: iomem range 0xf4005000-0xf4005fff has been reserved
[    0.312880] system 00:00: iomem range 0xf4006000-0xf4006fff has been reserved
[    0.312885] system 00:00: iomem range 0xf4008000-0xf400bfff has been reserved
[    0.312889] system 00:00: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.312899] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.312907] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.312911] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.312915] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.312919] system 00:03: ioport range 0x809-0x809 has been reserved
[    0.312929] system 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.312933] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.312937] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.312941] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.312945] system 00:08: ioport range 0x930-0x97f has been reserved
[    0.312954] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.347809] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.347816] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.347824] pci 0000:00:1c.0:   MEM window: 0xefd00000-0xefdfffff
[    0.347831] pci 0000:00:1c.0:   PREFETCH window: 0x00000080000000-0x000000801fffff
[    0.347841] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0c
[    0.347846] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.347854] pci 0000:00:1c.3:   MEM window: 0xefa00000-0xefcfffff
[    0.347860] pci 0000:00:1c.3:   PREFETCH window: 0x000000e0000000-0x000000e01fffff
[    0.347871] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.347874] pci 0000:00:1e.0:   IO window: disabled
[    0.347882] pci 0000:00:1e.0:   MEM window: 0xef900000-0xef9fffff
[    0.347888] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.347916]   alloc irq_desc for 16 on node -1
[    0.347919]   alloc kstat_irqs on node -1
[    0.347930] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.347938] pci 0000:00:1c.0: setting latency timer to 64
[    0.347951]   alloc irq_desc for 19 on node -1
[    0.347953]   alloc kstat_irqs on node -1
[    0.347958] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.347964] pci 0000:00:1c.3: setting latency timer to 64
[    0.347976] pci 0000:00:1e.0: setting latency timer to 64
[    0.347983] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.347986] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.347990] pci_bus 0000:0b: resource 0 io:  [0x2000-0x2fff]
[    0.347994] pci_bus 0000:0b: resource 1 mem: [0xefd00000-0xefdfffff]
[    0.347998] pci_bus 0000:0b: resource 2 pref mem [0x80000000-0x801fffff]
[    0.348002] pci_bus 0000:0c: resource 0 io:  [0xd000-0xdfff]
[    0.348005] pci_bus 0000:0c: resource 1 mem: [0xefa00000-0xefcfffff]
[    0.348009] pci_bus 0000:0c: resource 2 pref mem [0xe0000000-0xe01fffff]
[    0.348013] pci_bus 0000:03: resource 1 mem: [0xef900000-0xef9fffff]
[    0.348017] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.348020] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.348080] NET: Registered protocol family 2
[    0.348217] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.348652] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.349506] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.349919] TCP: Hash tables configured (established 131072 bind 65536)
[    0.349922] TCP reno registered
[    0.350066] NET: Registered protocol family 1
[    0.350094] pci 0000:00:02.0: Boot video device
[    0.350117]   alloc irq_desc for 20 on node -1
[    0.350120]   alloc kstat_irqs on node -1
[    0.350129] pci 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.350154] pci 0000:00:1d.0: PCI INT A disabled
[    0.350163]   alloc irq_desc for 21 on node -1
[    0.350165]   alloc kstat_irqs on node -1
[    0.350171] pci 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.350194] pci 0000:00:1d.1: PCI INT B disabled
[    0.350202]   alloc irq_desc for 22 on node -1
[    0.350205]   alloc kstat_irqs on node -1
[    0.350209] pci 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.350233] pci 0000:00:1d.2: PCI INT C disabled
[    0.350241]   alloc irq_desc for 23 on node -1
[    0.350244]   alloc kstat_irqs on node -1
[    0.350248] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.350272] pci 0000:00:1d.3: PCI INT D disabled
[    0.350288] pci 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.350320] pci 0000:00:1d.7: PCI INT A disabled
[    0.350371] Simple Boot Flag at 0x79 set to 0x1
[    0.350605] cpufreq-nforce2: No nForce2 chipset.
[    0.350643] Scanning for low memory corruption every 60 seconds
[    0.350811] audit: initializing netlink socket (disabled)
[    0.350826] type=2000 audit(1335437160.348:1): initialized
[    0.364044] highmem bounce pool size: 64 pages
[    0.364052] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.366332] VFS: Disk quotas dquot_6.5.2
[    0.366423] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.367244] fuse init (API version 7.13)
[    0.367365] msgmni has been set to 1690
[    0.367645] alg: No test for stdrng (krng)
[    0.367720] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.367724] io scheduler noop registered
[    0.367727] io scheduler anticipatory registered
[    0.367729] io scheduler deadline registered
[    0.367789] io scheduler cfq registered (default)
[    0.367997]   alloc irq_desc for 24 on node -1
[    0.368001]   alloc kstat_irqs on node -1
[    0.368018] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.368032] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.368221]   alloc irq_desc for 25 on node -1
[    0.368224]   alloc kstat_irqs on node -1
[    0.368235] pcieport 0000:00:1c.3: irq 25 for MSI/MSI-X
[    0.368247] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.368378] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.368481] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.368996] ACPI: AC Adapter [AC] (on-line)
[    0.369127] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.369539] ACPI: Lid Switch [LID]
[    0.369601] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.369608] ACPI: Power Button [PBTN]
[    0.369669] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.369673] ACPI: Sleep Button [SBTN]
[    0.370506] ACPI: SSDT 7f6d4134 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.370951] ACPI: SSDT 7f6d3ee9 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.371496] processor LNXCPU:00: registered as cooling_device0
[    0.371959] ACPI: SSDT 7f6d4378 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.372379] ACPI: SSDT 7f6d40af 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.372828] processor LNXCPU:01: registered as cooling_device1
[    0.380229] thermal LNXTHERM:01: registered as thermal_zone0
[    0.380241] ACPI: Thermal Zone [THM] (63 C)
[    0.382350] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.384201] brd: module loaded
[    0.384870] loop: module loaded
[    0.384983] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.385134] ata_piix 0000:00:1f.2: version 2.13
[    0.385158]   alloc irq_desc for 17 on node -1
[    0.385160]   alloc kstat_irqs on node -1
[    0.385170] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.385178] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.385235] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.385347] scsi0 : ata_piix
[    0.385450] scsi1 : ata_piix
[    0.386507] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.386511] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.387203] Fixed MDIO Bus: probed
[    0.387253] PPP generic driver version 2.4.2
[    0.387301] tun: Universal TUN/TAP device driver, 1.6
[    0.387304] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.387526] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.387669] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.387690] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.387695] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.387747] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.387781] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.387796] ehci_hcd 0000:00:1d.7: debug port 1
[    0.391789] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.391833] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.395762] isapnp: Scanning for PnP cards...
[    0.440461] ACPI: Battery Slot [BAT0] (battery present)
[    0.446907] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.447069] usb usb1: configuration #1 chosen from 1 choice
[    0.447111] hub 1-0:1.0: USB hub found
[    0.447125] hub 1-0:1.0: 8 ports detected
[    0.447221] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.447247] uhci_hcd: USB Universal Host Controller Interface driver
[    0.447308] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.447322] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.447327] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.447378] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.447416] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.447539] usb usb2: configuration #1 chosen from 1 choice
[    0.447573] hub 2-0:1.0: USB hub found
[    0.447584] hub 2-0:1.0: 2 ports detected
[    0.447642] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.447652] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.447656] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.447701] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.447747] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.447867] usb usb3: configuration #1 chosen from 1 choice
[    0.447902] hub 3-0:1.0: USB hub found
[    0.447911] hub 3-0:1.0: 2 ports detected
[    0.447973] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.447983] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.447988] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.448030] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.448074] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.448191] usb usb4: configuration #1 chosen from 1 choice
[    0.448226] hub 4-0:1.0: USB hub found
[    0.448236] hub 4-0:1.0: 2 ports detected
[    0.448305] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.448314] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.448319] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.448361] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.448401] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.448523] usb usb5: configuration #1 chosen from 1 choice
[    0.448558] hub 5-0:1.0: USB hub found
[    0.448566] hub 5-0:1.0: 2 ports detected
[    0.448698] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.451244] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.451256] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.451434] mice: PS/2 mouse device common for all mice
[    0.451615] rtc_cmos 00:06: RTC can wake from S4
[    0.451667] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.451706] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.451865] device-mapper: uevent: version 1.0.3
[    0.456233] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.495730] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.496257] Freeing initrd memory: 7808k freed
[    0.540064] device-mapper: multipath: version 1.1.0 loaded
[    0.540070] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.540318] EISA: Probing bus 0 at eisa.0
[    0.540331] Cannot allocate resource for EISA slot 1
[    0.540334] Cannot allocate resource for EISA slot 2
[    0.540363] EISA: Detected 0 cards.
[    0.540585] cpuidle: using governor ladder
[    0.540754] cpuidle: using governor menu
[    0.541332] TCP cubic registered
[    0.541554] NET: Registered protocol family 10
[    0.542615] NET: Registered protocol family 17
[    0.543609] Using IPI No-Shortcut mode
[    0.543731] PM: Resume from disk failed.
[    0.543748] registered taskstats version 1
[    0.544337]   Magic number: 8:237:781
[    0.544465] rtc_cmos 00:06: setting system clock to 2012-04-26 10:46:01 UTC (1335437161)
[    0.544470] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.544472] EDD information not available.
[    0.565268] ata1.00: ATA-8: WDC WD3200BEKT-00F3T0, 11.01A11, max UDMA/133
[    0.565273] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.573291] ata1.00: configured for UDMA/133
[    0.605424] ata2.00: ATAPI: SONY DVD+/-RW DW-Q58A, UDS2, max UDMA/33
[    0.621337] ata2.00: configured for UDMA/33
[    0.757382] isapnp: No Plug & Play device found
[    0.757589] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-0 11.0 PQ: 0 ANSI: 5
[    0.757765] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    0.757769] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.757840] sd 0:0:0:0: [sda] Write Protect is off
[    0.757844] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.757937] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.758332]  sda:
[    0.758537] scsi 1:0:0:0: CD-ROM            SONY     DVD+-RW DW-Q58A  UDS2 PQ: 0 ANSI: 5
[    0.762173] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.762181] Uniform CD-ROM driver Revision: 3.20
[    0.762382] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.762510] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.795181]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    0.860980] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.861021] Freeing unused kernel memory: 664k freed
[    0.861550] Write protecting the kernel text: 4700k
[    0.861622] Write protecting the kernel read-only data: 1848k
[    0.882036] udev: starting version 151
[    1.072573] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.136119] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.136154] b44.c:v2.0
[    1.136194] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.157166] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:25:f4:7a
[    1.194272] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.517684] EXT3-fs: INFO: recovery required on readonly filesystem.
[    1.517692] EXT3-fs: write access will be enabled during recovery.
[    2.468651] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc00037b7ad41]
[    2.528835] kjournald starting.  Commit interval 5 seconds
[    2.528875] EXT3-fs: sda10: orphan cleanup on readonly fs
[    2.528883] ext3_orphan_cleanup: deleting unreferenced inode 565286
[    2.528914] ext3_orphan_cleanup: deleting unreferenced inode 565282
[    2.528925] ext3_orphan_cleanup: deleting unreferenced inode 565277
[    2.528934] ext3_orphan_cleanup: deleting unreferenced inode 565273
[    2.528943] ext3_orphan_cleanup: deleting unreferenced inode 565259
[    2.528951] EXT3-fs: sda10: 5 orphan inodes deleted
[    2.528953] EXT3-fs: recovery complete.
[    2.531152] EXT3-fs: mounted filesystem with ordered data mode.
[   23.287076] udev: starting version 151
[   23.396421] Adding 1614492k swap on /dev/sda5.  Priority:-1 extents:1 across:1614492k 
[   23.442677] lp: driver loaded but no devices found
[   23.637408] cfg80211: Calling CRDA to update world regulatory domain
[   23.641785] acpi device:27: registered as cooling_device2
[   23.644518] EXT3 FS on sda10, internal journal
[   23.644641] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input5
[   23.645444] Linux agpgart interface v0.103
[   23.654895] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   23.655011] ACPI Warning for \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) (20090903/nspredef-433)
[   23.655610] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:02/input/input6
[   23.656039] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   23.676805] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   23.677727] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   23.686494] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   23.719141] intel_rng: FWH not detected
[   23.721810] cfg80211: World regulatory domain updated:
[   23.721814]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.721819]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.721824]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.721827]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.721831]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.721835]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.733152] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   23.762655] sdhci: Secure Digital Host Controller Interface driver
[   23.762660] sdhci: Copyright(c) Pierre Ossman
[   23.765153] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[   23.765178]   alloc irq_desc for 18 on node -1
[   23.765181]   alloc kstat_irqs on node -1
[   23.765191] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   23.767525] Registered led device: mmc0::
[   23.768884] [drm] Initialized drm 1.1.0 20060810
[   23.768895] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   23.802102] type=1505 audit(1335451584.755:2):  operation="profile_load" pid=644 name="/sbin/dhclient3"
[   23.802920] type=1505 audit(1335451584.755:3):  operation="profile_load" pid=644 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.803374] type=1505 audit(1335451584.755:4):  operation="profile_load" pid=644 name="/usr/lib/connman/scripts/dhclient-script"
[   23.889346] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   23.932849] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.932857] i915 0000:00:02.0: setting latency timer to 64
[   23.936767] [drm] set up 7M of stolen space
[   23.954802] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   23.954807] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   23.954938] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.954954] iwl3945 0000:0b:00.0: setting latency timer to 64
[   24.051759] composite sync not supported
[   24.052213] [drm] initialized overlay support
[   24.070568] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   24.070574] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   24.070704]   alloc irq_desc for 26 on node -1
[   24.070707]   alloc kstat_irqs on node -1
[   24.070746] iwl3945 0000:0b:00.0: irq 26 for MSI/MSI-X
[   24.143052] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   24.384265] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000/0x0
[   24.425609] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   24.443164] composite sync not supported
[   24.568150] fb0: inteldrmfb frame buffer device
[   24.568155] registered panic notifier
[   24.568166] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.568229] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   24.568256] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.571221] vga16fb: initializing
[   24.571226] vga16fb: mapped to 0xc00a0000
[   24.571230] vga16fb: not registering due to another framebuffer present
[   24.697699] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   24.697948] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   24.718132] Console: switching to colour frame buffer device 160x50
[   24.855042] composite sync not supported
[   25.467717] REISERFS (device sda6): found reiserfs format "3.6" with standard journal
[   25.467738] REISERFS (device sda6): using ordered data mode
[   25.472031] REISERFS (device sda6): journal params: device sda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   25.472379] REISERFS (device sda6): checking transaction log (sda6)
[   25.498462] REISERFS (device sda6): Using r5 hash to sort names
[   25.643501] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   25.659495] type=1505 audit(1335451586.611:5):  operation="profile_replace" pid=908 name="/sbin/dhclient3"
[   25.660332] type=1505 audit(1335451586.615:6):  operation="profile_replace" pid=908 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.660796] type=1505 audit(1335451586.615:7):  operation="profile_replace" pid=908 name="/usr/lib/connman/scripts/dhclient-script"
[   25.663787] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[   25.675448] type=1505 audit(1335451586.627:8):  operation="profile_load" pid=907 name="/usr/share/gdm/guest-session/Xsession"
[   25.687785] type=1505 audit(1335451586.639:9):  operation="profile_load" pid=979 name="/usr/lib/cups/backend/cups-pdf"
[   25.688821] type=1505 audit(1335451586.643:10):  operation="profile_load" pid=979 name="/usr/sbin/cupsd"
[   25.696120] type=1505 audit(1335451586.651:11):  operation="profile_load" pid=976 name="/usr/bin/evince"
[   25.743793] Registered led device: iwl-phy0::radio
[   25.744528] Registered led device: iwl-phy0::assoc
[   25.744605] Registered led device: iwl-phy0::RX
[   25.744857] Registered led device: iwl-phy0::TX
[   25.757064] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.762883] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.044860] composite sync not supported
[   26.466633] composite sync not supported
[   27.870793] composite sync not supported
[   28.289819] composite sync not supported
[   28.721522] composite sync not supported
[   28.937072] device eth0 entered promiscuous mode
[   28.969066] device eth0 left promiscuous mode
[   28.996052] device eth0 entered promiscuous mode
[   29.228511] ppdev: user-space parallel port driver
[   30.323898] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   37.160281] composite sync not supported
[   37.618091] composite sync not supported
[  142.248732] Registered led device: iwl-phy0::radio
[  142.248761] Registered led device: iwl-phy0::assoc
[  142.248786] Registered led device: iwl-phy0::RX
[  142.248810] Registered led device: iwl-phy0::TX
[  142.269263] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1034.303133] grub-probe: sending ioctl 1261 to a partition!
[ 1034.303142] grub-probe: sending ioctl 1261 to a partition!
[ 1034.333803] grub-probe: sending ioctl 1261 to a partition!
[ 1034.333811] grub-probe: sending ioctl 1261 to a partition!
[ 1034.367535] grub-probe: sending ioctl 1261 to a partition!
[ 1034.367544] grub-probe: sending ioctl 1261 to a partition!
[ 1034.371843] grub-probe: sending ioctl 1261 to a partition!
[ 1034.371851] grub-probe: sending ioctl 1261 to a partition!
[ 1034.425661] grub-probe: sending ioctl 1261 to a partition!
[ 1034.425670] grub-probe: sending ioctl 1261 to a partition!
[ 1035.616909] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 1035.619553] SGI XFS Quota Management subsystem
[ 1035.639606] JFS: nTxBlock = 8192, nTxLock = 65536
[ 1035.682384] NTFS driver 2.1.29 [Flags: R/O MODULE].
[ 1035.719572] QNX4 filesystem 0.2.3 registered.
[ 1035.802085] Btrfs loaded
[ 1036.476677] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 1036.476762] REISERFS (device sda7): using ordered data mode
[ 1036.479597] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1036.480157] REISERFS (device sda7): checking transaction log (sda7)
[ 1036.509829] REISERFS (device sda7): Using r5 hash to sort names
[ 1037.628868] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 1037.628954] REISERFS (device sda7): using ordered data mode
[ 1037.636149] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1037.636674] REISERFS (device sda7): checking transaction log (sda7)
[ 1037.666381] REISERFS (device sda7): Using r5 hash to sort names
[ 1039.725333] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 1039.725420] REISERFS (device sda7): using ordered data mode
[ 1039.733038] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1039.733558] REISERFS (device sda7): checking transaction log (sda7)
[ 1039.763130] REISERFS (device sda7): Using r5 hash to sort names
[ 1040.568436] __ratelimit: 194 callbacks suppressed
[ 1040.568445] grub-probe: sending ioctl 1261 to a partition!
[ 1040.568451] grub-probe: sending ioctl 1261 to a partition!
[ 1040.599126] grub-probe: sending ioctl 1261 to a partition!
[ 1040.599135] grub-probe: sending ioctl 1261 to a partition!
[ 1040.631429] grub-probe: sending ioctl 1261 to a partition!
[ 1040.631437] grub-probe: sending ioctl 1261 to a partition!
[ 1040.636128] grub-probe: sending ioctl 1261 to a partition!
[ 1040.636135] grub-probe: sending ioctl 1261 to a partition!
[ 1040.637554] grub-probe: sending ioctl 1261 to a partition!
[ 1040.637562] grub-probe: sending ioctl 1261 to a partition!
[ 1040.756828] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 1040.756923] REISERFS (device sda7): using ordered data mode
[ 1040.764644] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1040.765178] REISERFS (device sda7): checking transaction log (sda7)
[ 1040.766563] REISERFS (device sda7): Using r5 hash to sort names
[ 1046.190604] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 1046.190694] REISERFS (device sda7): using ordered data mode
[ 1046.197881] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1046.198406] REISERFS (device sda7): checking transaction log (sda7)
[ 1046.228120] REISERFS (device sda7): Using r5 hash to sort names
[ 1047.075031] __ratelimit: 110 callbacks suppressed
[ 1047.075039] grub-probe: sending ioctl 1261 to a partition!
[ 1047.075046] grub-probe: sending ioctl 1261 to a partition!
[ 1047.105673] grub-probe: sending ioctl 1261 to a partition!
[ 1047.105681] grub-probe: sending ioctl 1261 to a partition!
[ 1047.138097] grub-probe: sending ioctl 1261 to a partition!
[ 1047.138105] grub-probe: sending ioctl 1261 to a partition!
[ 1047.142749] grub-probe: sending ioctl 1261 to a partition!
[ 1047.142757] grub-probe: sending ioctl 1261 to a partition!
[ 1047.144284] grub-probe: sending ioctl 1261 to a partition!
[ 1047.144292] grub-probe: sending ioctl 1261 to a partition!
[ 1047.263374] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 1047.263466] REISERFS (device sda7): using ordered data mode
[ 1047.271222] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1047.271757] REISERFS (device sda7): checking transaction log (sda7)
[ 1047.273297] REISERFS (device sda7): Using r5 hash to sort names
[ 1049.194501] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 1049.194591] REISERFS (device sda7): using ordered data mode
[ 1049.201573] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1049.202105] REISERFS (device sda7): checking transaction log (sda7)
[ 1049.231800] REISERFS (device sda7): Using r5 hash to sort names
[ 1050.283742] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 1050.283834] REISERFS (device sda7): using ordered data mode
[ 1050.291539] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1050.292122] REISERFS (device sda7): checking transaction log (sda7)
[ 1050.293510] REISERFS (device sda7): Using r5 hash to sort names
[ 1079.990685] __ratelimit: 146 callbacks suppressed
[ 1079.990694] grub-probe: sending ioctl 1261 to a partition!
[ 1079.990701] grub-probe: sending ioctl 1261 to a partition!
[ 1080.021341] grub-probe: sending ioctl 1261 to a partition!
[ 1080.021349] grub-probe: sending ioctl 1261 to a partition!
[ 1080.056363] grub-probe: sending ioctl 1261 to a partition!
[ 1080.056371] grub-probe: sending ioctl 1261 to a partition!
[ 1080.061017] grub-probe: sending ioctl 1261 to a partition!
[ 1080.061025] grub-probe: sending ioctl 1261 to a partition!
[ 1080.113281] grub-probe: sending ioctl 1261 to a partition!
[ 1080.113290] grub-probe: sending ioctl 1261 to a partition!
[ 1081.419268] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 1081.419384] REISERFS (device sda7): using ordered data mode
[ 1081.426647] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1081.427176] REISERFS (device sda7): checking transaction log (sda7)
[ 1081.456877] REISERFS (device sda7): Using r5 hash to sort names
[ 1082.463137] REISERFS (device sda7): found reiserfs format "3.6" with standard journal
[ 1082.463233] REISERFS (device sda7): using ordered data mode
[ 1082.475021] REISERFS (device sda7): journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[ 1082.475581] REISERFS (device sda7): checking transaction log (sda7)
[ 1082.477137] REISERFS (device sda7): Using r5 hash to sort names

---

### Post by gordintoronto on 2012-04-26
Step 1: change the ssid of your router! A nice, simple lower-case name which does not identify you is much better, and is probably required to make it work in 10.04. How about: toronto

It appears that your wireless card sees your router, so it is working and has an appropriate driver.

Have you ever set up a wireless connection? 12.04 is substantially improved over 10.04, but this should work:
 - right-click on the network icon on the top-right of your screen
 - select "Edit connections"
 - select the wireless tab and "add" (this is from memory, so it might not be 100%)
 - type in the ssid of your router, make sure "all users" is clicked
 - select the security tab, select wpa (assuming your router is set up properly) enter the wpa password.
 - OK or "apply" and OK until you're done.

---

### Post by dalexnagy on 2012-04-26
SOLVED!  

I am using LXDE for my desktop manager.  I found that if I used another desktop manager (XUBUNTU, XFCD, Gnome, Netbook), the wireless connection worked PERFECTLY!  Adding LXDE to the search terms found the solution.

I had to add '@nm-applet' to the LXDE startup configuration ([FONT=Courier New]/etc/xdg/lxsession/LXDE/autostart)[FONT=Verdana], logoff, choose LXDE, and logon.  Voila, I am connected wirelessly!

In summary, this was an LXDE issue, not a Ubuntu issue.
[/FONT][/FONT]

---

