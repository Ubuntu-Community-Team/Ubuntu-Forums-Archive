---
title: "USB3 disks intermittently not recognized."
date: 2017-01-27
forum: Hardware
---

### Post by jjv on 2017-01-27
I have two large Western Digital USB3 external hard drives (no external power supply) that will intermittently not be detected by Ubuntu 16.04 (fresh install, latest patches and kernel) when using a USB3 port. The drives are 2TB and 4TB capacity.

If I plug in a 4 port USB2 hub into the USB3 port (any of them) both drives are seen correctly and consistently.

The hardware is a Dell 7710 notebook with 4 USB3 ports with power share.

There does not seem to be an issue when I use a small USB3 thumb drive (128 GB), only when I use the larger external drives.

When the drives fail, the system does even see them. No entries in any log files and no device nodes created (/dev/sd*). The light on the drive comes on but remains solid. When the drive mounts the light will begin to flash as it communicates with the OS.

I am not certain if this is a power issue (I doubt it since I can successfully use both drives simultaneously on the USB2 hub) or if this is a kernel issue communicating with the larger external USB3 drives.

My google and ubuntu searches have not come up with anything definitive.

lsusb
Bus 002 Device 002: ID 0424:5534 Standard Microsystems Corp. Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 006: ID 0e8d:1887 MediaTek Inc. 
Bus 001 Device 009: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 010: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 001 Device 007: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 004: ID 0424:2134 Standard Microsystems Corp. Hub
Bus 001 Device 002: ID 0424:2134 Standard Microsystems Corp. Hub
Bus 001 Device 008: ID 1bcf:28b8 Sunplus Innovation Technology Inc. 
Bus 001 Device 005: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 001 Device 013: ID 1058:10b8 Western Digital Technologies, Inc. Elements Portable (WDBU6Y, WDBUZG)
Bus 001 Device 014: ID 1058:2599 Western Digital Technologies, Inc. 
Bus 001 Device 011: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lspci
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #2 (rev f1)
00:1c.2 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #3 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-LM (rev 31)
01:00.0 VGA compatible controller: NVIDIA Corporation GM204GLM [Quadro M5000M] (rev a1)
02:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)


Any pointers or suggestions are welcome.

---

### Post by ajgreeny on 2017-01-27
Duplicate of [https://ubuntuforums.org/showthread.php?t=2350758&p=13599941#post13599941](https://ubuntuforums.org/showthread.php?t=2350758&p=13599941#post13599941)

Thread closed.

---

### Post by cariboo on 2017-01-27
> **ajgreeny said:**
> Duplicate of [https://ubuntuforums.org/showthread.php?t=2350758&p=13599941#post13599941](https://ubuntuforums.org/showthread.php?t=2350758&p=13599941#post13599941)

Thread closed.

Closed the other thread that was still open. We will leave this one open.

---

