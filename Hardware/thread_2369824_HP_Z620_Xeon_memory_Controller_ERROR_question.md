---
title: "HP Z620 Xeon memory Controller ERROR question ?"
date: 2017-08-27
forum: Hardware
---

### Post by gipag on 2017-08-27
i have one HP Z620 Dual Xeon 32GB Ram Ubuntu 17.04
after launched ```
$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E5/Core i7 DMI2 (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 1a (rev 06)
00:02.0 PCI bridge: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 2a (rev 06)
00:03.0 PCI bridge: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 3a in PCI Express Mode (rev 06)
00:05.0 System peripheral: Intel Corporation Xeon E5/Core i7 Address Map, VTd_Misc, System Management (rev 06)
00:05.2 System peripheral: Intel Corporation Xeon E5/Core i7 Control Status and Global Errors (rev 06)
00:05.4 PIC: Intel Corporation Xeon E5/Core i7 I/O APIC (rev 06)
00:11.0 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Virtual Root Port (rev 05)
00:16.0 Communication controller: Intel Corporation C600/X79 series chipset MEI Controller #1 (rev 05)
00:16.2 IDE interface: Intel Corporation C600/X79 series chipset IDE-r Controller (rev 05)
00:16.3 Serial controller: Intel Corporation C600/X79 series chipset KT Controller (rev 05)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation C600/X79 series chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 5 (rev b5)
00:1c.6 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 3 (rev b5)
00:1c.7 PCI bridge: Intel Corporation C600/X79 series chipset PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation C600/X79 series chipset LPC Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation C600/X79 series chipset SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation C600/X79 series chipset SMBus Host Controller (rev 05)
01:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
02:00.0 Serial Attached SCSI controller: Intel Corporation C602 chipset 4-Port SATA Storage Control Unit (rev 05)
04:00.0 VGA compatible controller: NVIDIA Corporation GF108GL [Quadro 600] (rev a1)
04:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
05:00.0 VGA compatible controller: NVIDIA Corporation GP104 [GeForce GTX 1080] (rev a1)
05:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)
08:00.0 USB controller: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller (rev 02)
09:05.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)
3f:08.0 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link 0 (rev 06)
3f:08.3 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 (rev 06)
3f:08.4 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 (rev 06)
3f:09.0 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link 1 (rev 06)
3f:09.3 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 (rev 06)
3f:09.4 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 (rev 06)
3f:0a.0 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 (rev 06)
3f:0a.1 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 (rev 06)
3f:0a.2 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 (rev 06)
3f:0a.3 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 (rev 06)
3f:0b.0 System peripheral: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers (rev 06)
3f:0b.3 System peripheral: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers (rev 06)
3f:0c.0 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
3f:0c.1 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
3f:0c.2 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
3f:0c.3 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
3f:0c.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 (rev 06)
3f:0c.7 System peripheral: Intel Corporation Xeon E5/Core i7 System Address Decoder (rev 06)
3f:0d.0 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
3f:0d.1 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
3f:0d.2 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
3f:0d.3 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
3f:0d.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 (rev 06)
3f:0e.0 System peripheral: Intel Corporation Xeon E5/Core i7 Processor Home Agent (rev 06)
3f:0e.1 Performance counters: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring (rev 06)
3f:0f.0 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers (rev 06)
3f:0f.1 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers (rev 06)
3f:0f.2 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 (rev 06)
3f:0f.3 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 (rev 06)
3f:0f.4 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 (rev 06)
3f:0f.5 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 (rev 06)
3f:0f.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 (rev 06)
3f:10.0 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 (rev 06)
3f:10.1 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 (rev 06)
[COLOR=#ff0000]3f:10.2 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 (rev 06)[/COLOR]
[COLOR=#ff0000]3f:10.3 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 (rev 06)[/COLOR]
3f:10.4 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 2 (rev 06)
3f:10.5 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 (rev 06)
[COLOR=#ff0000]3f:10.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 (rev 06)[/COLOR]
[COLOR=#ff0000]3f:10.7 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 (rev 06)[/COLOR]
3f:11.0 System peripheral: Intel Corporation Xeon E5/Core i7 DDRIO (rev 06)
3f:13.0 System peripheral: Intel Corporation Xeon E5/Core i7 R2PCIe (rev 06)
3f:13.1 Performance counters: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor (rev 06)
3f:13.4 Performance counters: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers (rev 06)
3f:13.5 Performance counters: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor (rev 06)
3f:13.6 System peripheral: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor (rev 06)
40:05.0 System peripheral: Intel Corporation Xeon E5/Core i7 Address Map, VTd_Misc, System Management (rev 06)
40:05.2 System peripheral: Intel Corporation Xeon E5/Core i7 Control Status and Global Errors (rev 06)
40:05.4 PIC: Intel Corporation Xeon E5/Core i7 I/O APIC (rev 06)
7f:08.0 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link 0 (rev 06)
7f:08.3 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 (rev 06)
7f:08.4 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 (rev 06)
7f:09.0 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link 1 (rev 06)
7f:09.3 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 (rev 06)
7f:09.4 System peripheral: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 (rev 06)
7f:0a.0 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 (rev 06)
7f:0a.1 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 (rev 06)
7f:0a.2 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 (rev 06)
7f:0a.3 System peripheral: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 (rev 06)
7f:0b.0 System peripheral: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers (rev 06)
7f:0b.3 System peripheral: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers (rev 06)
7f:0c.0 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
7f:0c.1 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
7f:0c.2 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
7f:0c.3 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
7f:0c.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 (rev 06)
7f:0c.7 System peripheral: Intel Corporation Xeon E5/Core i7 System Address Decoder (rev 06)
7f:0d.0 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
7f:0d.1 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
7f:0d.2 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
7f:0d.3 System peripheral: Intel Corporation Xeon E5/Core i7 Unicast Register 0 (rev 06)
7f:0d.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 (rev 06)
7f:0e.0 System peripheral: Intel Corporation Xeon E5/Core i7 Processor Home Agent (rev 06)
7f:0e.1 Performance counters: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring (rev 06)
7f:0f.0 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers (rev 06)
7f:0f.1 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers (rev 06)
7f:0f.2 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 (rev 06)
7f:0f.3 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 (rev 06)
7f:0f.4 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 (rev 06)
7f:0f.5 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 (rev 06)
7f:0f.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 (rev 06)
7f:10.0 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 (rev 06)
7f:10.1 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 (rev 06)
[COLOR=#ff0000]7f:10.2 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 (rev 06)[/COLOR]
[COLOR=#ff0000]7f:10.3 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 (rev 06)[/COLOR]
7f:10.4 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 2 (rev 06)
7f:10.5 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 (rev 06)
[COLOR=#ff0000]7f:10.6 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 (rev 06)[/COLOR]
[COLOR=#ff0000]7f:10.7 System peripheral: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 (rev 06)[/COLOR]
7f:11.0 System peripheral: Intel Corporation Xeon E5/Core i7 DDRIO (rev 06)
7f:13.0 System peripheral: Intel Corporation Xeon E5/Core i7 R2PCIe (rev 06)
7f:13.1 Performance counters: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor (rev 06)
7f:13.4 Performance counters: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers (rev 06)
7f:13.5 Performance counters: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor (rev 06)
7f:13.6 System peripheral: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor (rev 06)

```
I find 4 Memory Controller ERROR Is that relevant ?
where is the problem It could be some ram Bank ?

---

### Post by Yellow Pasque on 2017-08-27
There is no problem. You are misinterpreting the output. The error registers are devices. If you look at lspci output from other xeon e5 systems, you will see the same devices listed (google it).
[https://certification.ubuntu.com/certification/catalog/component/pci/8086:3cb2/](https://certification.ubuntu.com/certification/catalog/component/pci/8086:3cb2/)

---

### Post by gipag on 2017-08-28
Very well thanks for support Temüjin !
You've taken my doubts off me

---

