---
title: "Built in webcam not detected anymore since 2 weeks. Lenovo X1 Nano Gen 1 U23.04"
date: 2023-10-04
forum: Hardware
---

### Post by shizow on 2023-10-04
Hey

my built in webcam was working fine for 2 years with the various ubuntu versions. Around 2 weeks ago the camera stopped working and was not detected anymore.

what can i do?

```

user@thinkpad:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Device 9a12 (rev 01)
	Subsystem: Lenovo Device 22c7
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Tiger Lake-UP4 GT2 [Iris Xe Graphics] (rev 01) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Tiger Lake-UP4 GT2 [Iris Xe Graphics]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 166
	Region 0: Memory at 603c000000 (64-bit, non-prefetchable) [size=16M]
	Region 2: Memory at 4000000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 3000 [size=64]
	Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:04.0 Signal processing controller: Intel Corporation TigerLake-LP Dynamic Tuning Processor Participant (rev 01)
	Subsystem: Lenovo TigerLake-LP Dynamic Tuning Processor Participant
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 603d180000 (64-bit, non-prefetchable) [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: proc_thermal
	Kernel modules: processor_thermal_device_pci_legacy

00:06.0 PCI bridge: Intel Corporation 11th Gen Core Processor PCIe Controller (rev 01) (prog-if 00 [Normal decode])
	Subsystem: Lenovo 11th Gen Core Processor PCIe Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 120
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: [disabled] [16-bit]
	Memory behind bridge: bc200000-bc2fffff [size=1M] [32-bit]
	Prefetchable memory behind bridge: [disabled] [64-bit]
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:07.0 PCI bridge: Intel Corporation Tiger Lake-LP Thunderbolt 4 PCI Express Root Port #1 (rev 01) (prog-if 00 [Normal decode])
	Subsystem: Lenovo Tiger Lake-LP Thunderbolt 4 PCI Express Root Port
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 121
	Bus: primary=00, secondary=20, subordinate=49, sec-latency=0
	I/O behind bridge: 4000-4fff [size=4K] [16-bit]
	Memory behind bridge: b0000000-bc1fffff [size=194M] [32-bit]
	Prefetchable memory behind bridge: 6000000000-601bffffff [size=448M] [32-bit]
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:07.2 PCI bridge: Intel Corporation Tiger Lake-LP Thunderbolt 4 PCI Express Root Port #2 (rev 01) (prog-if 00 [Normal decode])
	Subsystem: Lenovo Tiger Lake-LP Thunderbolt 4 PCI Express Root Port
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 122
	Bus: primary=00, secondary=50, subordinate=79, sec-latency=0
	I/O behind bridge: 5000-5fff [size=4K] [16-bit]
	Memory behind bridge: a2000000-ae1fffff [size=194M] [32-bit]
	Prefetchable memory behind bridge: 6020000000-603bffffff [size=448M] [32-bit]
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:08.0 System peripheral: Intel Corporation GNA Scoring Accelerator module (rev 01)
	Subsystem: Lenovo GNA Scoring Accelerator module
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at 603d1eb000 (64-bit, non-prefetchable) [disabled] [size=4K]
	Capabilities: <access denied>

00:0a.0 Signal processing controller: Intel Corporation Tigerlake Telemetry Aggregator Driver (rev 01)
	Subsystem: Lenovo Tigerlake Telemetry Aggregator Driver
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: Memory at 603d1d0000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: intel_vsec
	Kernel modules: intel_vsec

00:0d.0 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 USB Controller (rev 01) (prog-if 30 [XHCI])
	Subsystem: Lenovo Tiger Lake-LP Thunderbolt 4 USB Controller
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin ? routed to IRQ 123
	Region 0: Memory at 603d1c0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci

00:0d.2 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 NHI #0 (rev 01) (prog-if 40 [USB4 Host Interface])
	Subsystem: Device 2222:1111
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 603d140000 (64-bit, non-prefetchable) [size=256K]
	Region 2: Memory at 603d1ea000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: thunderbolt
	Kernel modules: thunderbolt

00:0d.3 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 NHI #1 (rev 01) (prog-if 40 [USB4 Host Interface])
	Subsystem: Device 2222:1111
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 603d100000 (64-bit, non-prefetchable) [size=256K]
	Region 2: Memory at 603d1e9000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: thunderbolt
	Kernel modules: thunderbolt

00:12.0 Serial controller: Intel Corporation Tiger Lake-LP Integrated Sensor Hub (rev 20) (prog-if 00 [8250])
	Subsystem: Lenovo Tiger Lake-LP Integrated Sensor Hub
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 603d1b0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: intel_ish_ipc
	Kernel modules: intel_ish_ipc

00:14.0 USB controller: Intel Corporation Tiger Lake-LP USB 3.2 Gen 2x1 xHCI Host Controller (rev 20) (prog-if 30 [XHCI])
	Subsystem: Lenovo Tiger Lake-LP USB 3.2 Gen 2x1 xHCI Host Controller
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 140
	Region 0: Memory at 603d1a0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci_pci

00:14.2 RAM memory: Intel Corporation Tiger Lake-LP Shared SRAM (rev 20)
	Subsystem: Lenovo Tiger Lake-LP Shared SRAM
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: Memory at 603d1e0000 (64-bit, non-prefetchable) [disabled] [size=16K]
	Region 2: Memory at 603d1e8000 (64-bit, non-prefetchable) [disabled] [size=4K]
	Capabilities: <access denied>

00:14.3 Network controller: Intel Corporation Wi-Fi 6 AX201 (rev 20)
	Subsystem: Intel Corporation Wi-Fi 6 AX201
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 603d1dc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

00:15.0 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #0 (rev 20)
	Subsystem: Lenovo Tiger Lake-LP Serial IO I2C Controller
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 27
	Region 0: Memory at 4017000000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: intel-lpss
	Kernel modules: intel_lpss_pci

00:15.3 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #3 (rev 20)
	Subsystem: Lenovo Tiger Lake-LP Serial IO I2C Controller
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 30
	Region 0: Memory at 4017001000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: intel-lpss
	Kernel modules: intel_lpss_pci

00:16.0 Communication controller: Intel Corporation Tiger Lake-LP Management Engine Interface (rev 20)
	Subsystem: Lenovo Tiger Lake-LP Management Engine Interface
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 141
	Region 0: Memory at 603d1e5000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: mei_me
	Kernel modules: mei_me

00:1f.0 ISA bridge: Intel Corporation Device a087 (rev 20)
	Subsystem: Lenovo Device 22c7
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:1f.3 Audio device: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller (rev 20) (prog-if 80)
	Subsystem: Lenovo Tiger Lake-LP Smart Sound Technology Audio Controller
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 178
	Region 0: Memory at 603d1d8000 (64-bit, non-prefetchable) [size=16K]
	Region 4: Memory at 603d000000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: sof-audio-pci-intel-tgl
	Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl

00:1f.4 SMBus: Intel Corporation Tiger Lake-LP SMBus Controller (rev 20)
	Subsystem: Lenovo Tiger Lake-LP SMBus Controller
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 603d1e4000 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at efa0 [size=32]
	Kernel driver in use: i801_smbus
	Kernel modules: i2c_i801

00:1f.5 Serial bus controller: Intel Corporation Tiger Lake-LP SPI Controller (rev 20)
	Subsystem: Lenovo Tiger Lake-LP SPI Controller
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: Memory at a0800000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: intel-spi
	Kernel modules: spi_intel_pci

04:00.0 Non-Volatile memory controller: Sandisk Corp Device 5008 (rev 01) (prog-if 02 [NVM Express])
	Subsystem: Sandisk Corp Device 5008
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	NUMA node: 0
	Region 0: Memory at bc200000 (64-bit, non-prefetchable) [size=16K]
	Region 4: Memory at bc204000 (64-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: nvme
	Kernel modules: nvme

```

```

user@thinkpad:~$ inxi -Fxxxrz
System:
  Kernel: 6.2.0-33-generic arch: x86_64 bits: 64 compiler: N/A Desktop: GNOME
    v: 44.3 tk: GTK v: 3.24.37 wm: gnome-shell dm: GDM3 v: 44.0 Distro: Ubuntu
    23.04 (Lunar Lobster)
Machine:
  Type: Laptop System: LENOVO product: INVALID v: ThinkPad X1 Nano Gen 1
    serial: <superuser required> Chassis: type: 10 serial: <superuser required>
  Mobo: LENOVO model: INVALID v: SDK0K17763 WIN serial: <superuser required>
    UEFI: LENOVO v: N2TET64W (1.42 ) date: 04/01/2021
Battery:
  ID-1: BAT0 charge: 37.6 Wh (100.0%) condition: 37.6/48.2 Wh (78.0%)
    volts: 13.1 min: 11.6 model: Celxpert 5B10W13964 type: Li-poly
    serial: <filter> status: full cycles: 729
CPU:
  Info: quad core model: 11th Gen Intel Core i7-1160G7 bits: 64 type: MT MCP
    smt: enabled arch: Tiger Lake rev: 1 cache: L1: 320 KiB L2: 5 MiB L3: 12 MiB
  Speed (MHz): avg: 1692 high: 2100 min/max: 400/4400 cores: 1: 2100 2: 2100
    3: 1011 4: 1001 5: 2100 6: 1031 7: 2100 8: 2100 bogomips: 33792
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3
Graphics:
  Device-1: Intel Tiger Lake-UP4 GT2 [Iris Xe Graphics] vendor: Lenovo
    driver: i915 v: kernel arch: Gen-12.1 ports: active: eDP-1 empty: DP-1,
    DP-2, DP-3, DP-4, HDMI-A-1 bus-ID: 00:02.0 chip-ID: 8086:9a40
    class-ID: 0300
  Display: wayland server: X.org v: 1.21.1.7 with: Xwayland v: 22.1.8
    compositor: gnome-shell driver: X: loaded: modesetting unloaded: fbdev,vesa
    dri: iris gpu: i915 display-ID: 0
  Monitor-1: eDP-1 model-id: CSO 0x1303 res: 2160x1350 dpi: 196
    size: 280x175mm (11.02x6.89") diag: 330mm (13") modes: 2160x1350
  API: OpenGL v: 4.6 Mesa 23.0.4-0ubuntu1~23.04.1 renderer: Mesa Intel Xe
    Graphics (TGL GT2) direct-render: Yes
Audio:
  Device-1: Intel Tiger Lake-LP Smart Sound Audio vendor: Lenovo
    driver: sof-audio-pci-intel-tgl bus-ID: 00:1f.3 chip-ID: 8086:a0c8
    class-ID: 0403
  Sound API: ALSA v: k6.2.0-33-generic running: yes
  Sound Server-1: PipeWire v: 0.3.65 running: yes
Network:
  Device-1: Intel Wi-Fi 6 AX201 driver: iwlwifi v: kernel bus-ID: 00:14.3
    chip-ID: 8086:a0f0 class-ID: 0280
  IF: wlp0s20f3 state: up mac: <filter>
  IF-ID-1: nordlynx state: unknown speed: N/A duplex: N/A mac: N/A
Bluetooth:
  Device-1: Intel AX201 Bluetooth type: USB driver: btusb v: 0.8
    bus-ID: 3-10:4 chip-ID: 8087:0026 class-ID: e001
  Report: hciconfig ID: hci0 rfk-id: 3 state: up address: <filter> bt-v: 3.0
    lmp-v: 5.2 sub-v: 200f hci-v: 5.2 rev: 200f
Drives:
  Local Storage: total: 953.87 GiB used: 273.3 GiB (28.7%)
  ID-1: /dev/nvme0n1 vendor: Western Digital model: PC SN530
    SDBPMPZ-1T00-1001 size: 953.87 GiB speed: 31.6 Gb/s lanes: 4 type: SSD
    serial: <filter> rev: 21160001 temp: 49.9 C scheme: GPT
Partition:
  ID-1: / size: 914.69 GiB used: 272.72 GiB (29.8%) fs: ext4 dev: /dev/dm-1
    mapped: vgubuntu-root
  ID-2: /boot size: 703.1 MiB used: 302.4 MiB (43.0%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-3: /boot/efi size: 511 MiB used: 6.2 MiB (1.2%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: partition size: 976 MiB used: 287.8 MiB (29.5%)
    priority: -2 dev: /dev/dm-2 mapped: vgubuntu-swap_1
Sensors:
  System Temperatures: cpu: 45.0 C mobo: N/A
  Fan Speeds (RPM): fan-1: 4172
Repos:
  Packages: 2446 pm: dpkg pkgs: 2416 pm: snap pkgs: 30
  Active apt repos in: /etc/apt/sources.list
    1: deb http://archive.ubuntu.com/ubuntu lunar main restricted
    2: deb http://archive.ubuntu.com/ubuntu lunar-updates main restricted
    3: deb http://archive.ubuntu.com/ubuntu lunar universe
    4: deb http://archive.ubuntu.com/ubuntu lunar-updates universe
    5: deb http://archive.ubuntu.com/ubuntu lunar multiverse
    6: deb http://archive.ubuntu.com/ubuntu lunar-updates multiverse
    7: deb http://archive.ubuntu.com/ubuntu lunar-backports main restricted universe multiverse
    8: deb http://archive.ubuntu.com/ubuntu lunar-security main restricted
    9: deb http://archive.ubuntu.com/ubuntu lunar-security universe
    10: deb http://archive.ubuntu.com/ubuntu lunar-security multiverse
  Active apt repos in: /etc/apt/sources.list.d/google-chrome.list
    1: deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
  No active apt repos in: /etc/apt/sources.list.d/google.list
  No active apt repos in: /etc/apt/sources.list.d/insync.list
  No active apt repos in: /etc/apt/sources.list.d/jtaylor-ubuntu-keepass-hirsute.list
  Active apt repos in: /etc/apt/sources.list.d/microsoft-edge.list
    1: deb [arch=amd64] https://packages.microsoft.com/repos/edge/ stable main
  Active apt repos in: /etc/apt/sources.list.d/nordvpn.list
    1: deb https://repo.nordvpn.com//deb/nordvpn/debian stable main
  No active apt repos in: /etc/apt/sources.list.d/obsproject-ubuntu-obs-studio-impish.list
  Active apt repos in: /etc/apt/sources.list.d/signal-xenial.list
    1: deb [arch=amd64 signed-by=/usr/share/keyrings/signal-desktop-keyring.gpg] https://updates.signal.org/desktop/apt xenial main
  No active apt repos in: /etc/apt/sources.list.d/slack.list
Info:
  Processes: 349 Uptime: 20h 14m wakeups: 41679 Memory: 15.34 GiB
  used: 6.75 GiB (44.0%) Init: systemd v: 252 target: graphical (5)
  default: graphical Compilers: gcc: 12.3.0 alt: 11/12 Shell: Bash v: 5.2.15
  running-in: gnome-terminal inxi: 3.3.25

```

---

