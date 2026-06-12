---
title: "Think my mobo sound is dead... Trying to trouble shoot it"
date: 2014-02-10
forum: Hardware
---

### Post by juliushibert63 on 2014-02-10
&#8203;I'm trying to troubleshoot the sound on my motherboard as I suspect it may have died. I have a GA-Z77X-UP5-TH motherboard (which I think has 7.1 output if I remember correctly).

I'm running Ubuntu 12.10 LTS Live Drive to test the sound. I'm not getting any output from the green port on the back of the motherboard or via the attached case headphone port. 

My main OS is OS X and I've tried troubleshooting the sound through that with no luck despite lots of help from the great people at TonyMac86 Forums. 

Has anyone got any suggestions I could try?

In case it's any help heres the output from my lscpi, lsusb and dmesg.


```

$lspci


00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 660 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
63:00.0 PCI bridge: PLX Technology, Inc. PEX 8605 PCI Express 4-port Gen2 Switch (rev aa)
64:01.0 PCI bridge: PLX Technology, Inc. PEX 8605 PCI Express 4-port Gen2 Switch (rev aa)
64:02.0 PCI bridge: PLX Technology, Inc. PEX 8605 PCI Express 4-port Gen2 Switch (rev aa)
64:03.0 PCI bridge: PLX Technology, Inc. PEX 8605 PCI Express 4-port Gen2 Switch (rev aa)
67:00.0 Network controller: Qualcomm Atheros AR93xx Wireless Network Adapter (rev 01)
68:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)
69:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
6a:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 11)

```




```

$lsusb


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0a5c:21e8 Broadcom Corp. 
Bus 004 Device 002: ID 2109:0810  
Bus 004 Device 003: ID 2109:0810  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 004: ID 2109:0810  
Bus 002 Device 005: ID abcd:1234 Unknown 
Bus 002 Device 003: ID 0781:540c SanDisk Corp. 
Bus 001 Device 005: ID 05ac:0304 Apple, Inc. Optical USB Mouse [Mitsumi]
Bus 001 Device 006: ID 05ac:0221 Apple, Inc. Aluminum Keyboard (ISO)

```


```

$dmesg


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-15-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 (Ubuntu 3.11.0-15.25~precise1-generic 3.11.10)
[    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cd891fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cd892000-0x00000000cdabffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cdac0000-0x00000000cdac0fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cdac1000-0x00000000cdbf1fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cdbf2000-0x00000000cea94fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cea95000-0x00000000cea95fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cea96000-0x00000000cead8fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cead9000-0x00000000cf478fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cf479000-0x00000000cf7d6fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cf7d7000-0x00000000cf7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000042effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI=0xcdbd2000  ACPI 2.0=0xcdbd2000  SMBIOS=0xf04c0  MPS=0xfd440 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x0000000000058000) (0MB)
[    0.000000] efi: mem02: type=4, attr=0xf, range=[0x0000000000058000-0x0000000000059000) (0MB)
[    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000059000-0x000000000005f000) (0MB)
[    0.000000] efi: mem04: type=4, attr=0xf, range=[0x000000000005f000-0x0000000000060000) (0MB)
[    0.000000] efi: mem05: type=3, attr=0xf, range=[0x0000000000060000-0x000000000009f000) (0MB)
[    0.000000] efi: mem06: type=6, attr=0x800000000000000f, range=[0x000000000009f000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem07: type=2, attr=0xf, range=[0x0000000000100000-0x000000000069f000) (5MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x000000000069f000-0x0000000001000000) (9MB)
[    0.000000] efi: mem09: type=2, attr=0xf, range=[0x0000000001000000-0x0000000001100000) (1MB)
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x0000000001100000-0x0000000035c80000) (843MB)
[    0.000000] efi: mem11: type=2, attr=0xf, range=[0x0000000035c80000-0x0000000035c84000) (0MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x0000000035c84000-0x0000000035c88000) (0MB)
[    0.000000] efi: mem13: type=2, attr=0xf, range=[0x0000000035c88000-0x0000000036e3c000) (17MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000036e3c000-0x000000008d213000) (1379MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x000000008d213000-0x00000000bd523000) (771MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x00000000bd523000-0x00000000bd529000) (0MB)
[    0.000000] efi: mem17: type=2, attr=0xf, range=[0x00000000bd529000-0x00000000bd6c1000) (1MB)
[    0.000000] efi: mem18: type=1, attr=0xf, range=[0x00000000bd6c1000-0x00000000bd7f5000) (1MB)
[    0.000000] efi: mem19: type=7, attr=0xf, range=[0x00000000bd7f5000-0x00000000bfcef000) (36MB)
[    0.000000] efi: mem20: type=4, attr=0xf, range=[0x00000000bfcef000-0x00000000bfff0000) (3MB)
[    0.000000] efi: mem21: type=7, attr=0xf, range=[0x00000000bfff0000-0x00000000c02f1000) (3MB)
[    0.000000] efi: mem22: type=4, attr=0xf, range=[0x00000000c02f1000-0x00000000c041e000) (1MB)
[    0.000000] efi: mem23: type=7, attr=0xf, range=[0x00000000c041e000-0x00000000c0677000) (2MB)
[    0.000000] efi: mem24: type=4, attr=0xf, range=[0x00000000c0677000-0x00000000c085f000) (1MB)
[    0.000000] efi: mem25: type=7, attr=0xf, range=[0x00000000c085f000-0x00000000c0863000) (0MB)
[    0.000000] efi: mem26: type=4, attr=0xf, range=[0x00000000c0863000-0x00000000c0874000) (0MB)
[    0.000000] efi: mem27: type=7, attr=0xf, range=[0x00000000c0874000-0x00000000c0878000) (0MB)
[    0.000000] efi: mem28: type=4, attr=0xf, range=[0x00000000c0878000-0x00000000c088b000) (0MB)
[    0.000000] efi: mem29: type=7, attr=0xf, range=[0x00000000c088b000-0x00000000c0890000) (0MB)
[    0.000000] efi: mem30: type=4, attr=0xf, range=[0x00000000c0890000-0x00000000c08a7000) (0MB)
[    0.000000] efi: mem31: type=7, attr=0xf, range=[0x00000000c08a7000-0x00000000c08b1000) (0MB)
[    0.000000] efi: mem32: type=4, attr=0xf, range=[0x00000000c08b1000-0x00000000c08cb000) (0MB)
[    0.000000] efi: mem33: type=7, attr=0xf, range=[0x00000000c08cb000-0x00000000c08d5000) (0MB)
[    0.000000] efi: mem34: type=4, attr=0xf, range=[0x00000000c08d5000-0x00000000c0935000) (0MB)
[    0.000000] efi: mem35: type=7, attr=0xf, range=[0x00000000c0935000-0x00000000c0956000) (0MB)
[    0.000000] efi: mem36: type=4, attr=0xf, range=[0x00000000c0956000-0x00000000c0957000) (0MB)
[    0.000000] efi: mem37: type=7, attr=0xf, range=[0x00000000c0957000-0x00000000c0958000) (0MB)
[    0.000000] efi: mem38: type=4, attr=0xf, range=[0x00000000c0958000-0x00000000c0959000) (0MB)
[    0.000000] efi: mem39: type=7, attr=0xf, range=[0x00000000c0959000-0x00000000c0983000) (0MB)
[    0.000000] efi: mem40: type=4, attr=0xf, range=[0x00000000c0983000-0x00000000c0984000) (0MB)
[    0.000000] efi: mem41: type=7, attr=0xf, range=[0x00000000c0984000-0x00000000c09aa000) (0MB)
[    0.000000] efi: mem42: type=4, attr=0xf, range=[0x00000000c09aa000-0x00000000c09ab000) (0MB)
[    0.000000] efi: mem43: type=7, attr=0xf, range=[0x00000000c09ab000-0x00000000c09ba000) (0MB)
[    0.000000] efi: mem44: type=4, attr=0xf, range=[0x00000000c09ba000-0x00000000c09bb000) (0MB)
[    0.000000] efi: mem45: type=7, attr=0xf, range=[0x00000000c09bb000-0x00000000c09c3000) (0MB)
[    0.000000] efi: mem46: type=4, attr=0xf, range=[0x00000000c09c3000-0x00000000c09ce000) (0MB)
[    0.000000] efi: mem47: type=7, attr=0xf, range=[0x00000000c09ce000-0x00000000c09e7000) (0MB)
[    0.000000] efi: mem48: type=4, attr=0xf, range=[0x00000000c09e7000-0x00000000c09e8000) (0MB)
[    0.000000] efi: mem49: type=7, attr=0xf, range=[0x00000000c09e8000-0x00000000c0a6b000) (0MB)
[    0.000000] efi: mem50: type=4, attr=0xf, range=[0x00000000c0a6b000-0x00000000c0a6c000) (0MB)
[    0.000000] efi: mem51: type=7, attr=0xf, range=[0x00000000c0a6c000-0x00000000c0a6d000) (0MB)
[    0.000000] efi: mem52: type=4, attr=0xf, range=[0x00000000c0a6d000-0x00000000c0a6e000) (0MB)
[    0.000000] efi: mem53: type=7, attr=0xf, range=[0x00000000c0a6e000-0x00000000c0b73000) (1MB)
[    0.000000] efi: mem54: type=4, attr=0xf, range=[0x00000000c0b73000-0x00000000c0b87000) (0MB)
[    0.000000] efi: mem55: type=7, attr=0xf, range=[0x00000000c0b87000-0x00000000c0b8b000) (0MB)
[    0.000000] efi: mem56: type=4, attr=0xf, range=[0x00000000c0b8b000-0x00000000c0b9c000) (0MB)
[    0.000000] efi: mem57: type=7, attr=0xf, range=[0x00000000c0b9c000-0x00000000c0ba0000) (0MB)
[    0.000000] efi: mem58: type=4, attr=0xf, range=[0x00000000c0ba0000-0x00000000c0bb1000) (0MB)
[    0.000000] efi: mem59: type=7, attr=0xf, range=[0x00000000c0bb1000-0x00000000c0bb6000) (0MB)
[    0.000000] efi: mem60: type=4, attr=0xf, range=[0x00000000c0bb6000-0x00000000c0bcc000) (0MB)
[    0.000000] efi: mem61: type=7, attr=0xf, range=[0x00000000c0bcc000-0x00000000c0bd6000) (0MB)
[    0.000000] efi: mem62: type=4, attr=0xf, range=[0x00000000c0bd6000-0x00000000c0bf2000) (0MB)
[    0.000000] efi: mem63: type=7, attr=0xf, range=[0x00000000c0bf2000-0x00000000c0bfc000) (0MB)
[    0.000000] efi: mem64: type=4, attr=0xf, range=[0x00000000c0bfc000-0x00000000c0c45000) (0MB)
[    0.000000] efi: mem65: type=7, attr=0xf, range=[0x00000000c0c45000-0x00000000c0c6e000) (0MB)
[    0.000000] efi: mem66: type=4, attr=0xf, range=[0x00000000c0c6e000-0x00000000c0c84000) (0MB)
[    0.000000] efi: mem67: type=7, attr=0xf, range=[0x00000000c0c84000-0x00000000c0c86000) (0MB)
[    0.000000] efi: mem68: type=4, attr=0xf, range=[0x00000000c0c86000-0x00000000c0c9d000) (0MB)
[    0.000000] efi: mem69: type=7, attr=0xf, range=[0x00000000c0c9d000-0x00000000c0ca1000) (0MB)
[    0.000000] efi: mem70: type=4, attr=0xf, range=[0x00000000c0ca1000-0x00000000c0cb2000) (0MB)
[    0.000000] efi: mem71: type=7, attr=0xf, range=[0x00000000c0cb2000-0x00000000c0cb6000) (0MB)
[    0.000000] efi: mem72: type=4, attr=0xf, range=[0x00000000c0cb6000-0x00000000c0cc8000) (0MB)
[    0.000000] efi: mem73: type=7, attr=0xf, range=[0x00000000c0cc8000-0x00000000c0ccd000) (0MB)
[    0.000000] efi: mem74: type=4, attr=0xf, range=[0x00000000c0ccd000-0x00000000c0ce4000) (0MB)
[    0.000000] efi: mem75: type=7, attr=0xf, range=[0x00000000c0ce4000-0x00000000c0cee000) (0MB)
[    0.000000] efi: mem76: type=4, attr=0xf, range=[0x00000000c0cee000-0x00000000c0d08000) (0MB)
[    0.000000] efi: mem77: type=7, attr=0xf, range=[0x00000000c0d08000-0x00000000c0d12000) (0MB)
[    0.000000] efi: mem78: type=4, attr=0xf, range=[0x00000000c0d12000-0x00000000c0d5d000) (0MB)
[    0.000000] efi: mem79: type=7, attr=0xf, range=[0x00000000c0d5d000-0x00000000c0d7e000) (0MB)
[    0.000000] efi: mem80: type=4, attr=0xf, range=[0x00000000c0d7e000-0x00000000c0da9000) (0MB)
[    0.000000] efi: mem81: type=7, attr=0xf, range=[0x00000000c0da9000-0x00000000c0dad000) (0MB)
[    0.000000] efi: mem82: type=4, attr=0xf, range=[0x00000000c0dad000-0x00000000c0dbe000) (0MB)
[    0.000000] efi: mem83: type=7, attr=0xf, range=[0x00000000c0dbe000-0x00000000c0dc2000) (0MB)
[    0.000000] efi: mem84: type=4, attr=0xf, range=[0x00000000c0dc2000-0x00000000c0dd4000) (0MB)
[    0.000000] efi: mem85: type=7, attr=0xf, range=[0x00000000c0dd4000-0x00000000c0dd9000) (0MB)
[    0.000000] efi: mem86: type=4, attr=0xf, range=[0x00000000c0dd9000-0x00000000c0df0000) (0MB)
[    0.000000] efi: mem87: type=7, attr=0xf, range=[0x00000000c0df0000-0x00000000c0dfa000) (0MB)
[    0.000000] efi: mem88: type=4, attr=0xf, range=[0x00000000c0dfa000-0x00000000c0e13000) (0MB)
[    0.000000] efi: mem89: type=7, attr=0xf, range=[0x00000000c0e13000-0x00000000c0e1d000) (0MB)
[    0.000000] efi: mem90: type=4, attr=0xf, range=[0x00000000c0e1d000-0x00000000c0e7f000) (0MB)
[    0.000000] efi: mem91: type=7, attr=0xf, range=[0x00000000c0e7f000-0x00000000c0ea0000) (0MB)
[    0.000000] efi: mem92: type=4, attr=0xf, range=[0x00000000c0ea0000-0x00000000c0ebe000) (0MB)
[    0.000000] efi: mem93: type=7, attr=0xf, range=[0x00000000c0ebe000-0x00000000c0ec2000) (0MB)
[    0.000000] efi: mem94: type=4, attr=0xf, range=[0x00000000c0ec2000-0x00000000c0ed4000) (0MB)
[    0.000000] efi: mem95: type=7, attr=0xf, range=[0x00000000c0ed4000-0x00000000c0ed8000) (0MB)
[    0.000000] efi: mem96: type=4, attr=0xf, range=[0x00000000c0ed8000-0x00000000c0eea000) (0MB)
[    0.000000] efi: mem97: type=7, attr=0xf, range=[0x00000000c0eea000-0x00000000c0eef000) (0MB)
[    0.000000] efi: mem98: type=4, attr=0xf, range=[0x00000000c0eef000-0x00000000c0f06000) (0MB)
[    0.000000] efi: mem99: type=7, attr=0xf, range=[0x00000000c0f06000-0x00000000c0f10000) (0MB)
[    0.000000] efi: mem100: type=4, attr=0xf, range=[0x00000000c0f10000-0x00000000c0f2a000) (0MB)
[    0.000000] efi: mem101: type=7, attr=0xf, range=[0x00000000c0f2a000-0x00000000c0f34000) (0MB)
[    0.000000] efi: mem102: type=4, attr=0xf, range=[0x00000000c0f34000-0x00000000c1007000) (0MB)
[    0.000000] efi: mem103: type=7, attr=0xf, range=[0x00000000c1007000-0x00000000c100b000) (0MB)
[    0.000000] efi: mem104: type=4, attr=0xf, range=[0x00000000c100b000-0x00000000c101c000) (0MB)
[    0.000000] efi: mem105: type=7, attr=0xf, range=[0x00000000c101c000-0x00000000c1020000) (0MB)
[    0.000000] efi: mem106: type=4, attr=0xf, range=[0x00000000c1020000-0x00000000c1031000) (0MB)
[    0.000000] efi: mem107: type=7, attr=0xf, range=[0x00000000c1031000-0x00000000c1036000) (0MB)
[    0.000000] efi: mem108: type=4, attr=0xf, range=[0x00000000c1036000-0x00000000c104c000) (0MB)
[    0.000000] efi: mem109: type=7, attr=0xf, range=[0x00000000c104c000-0x00000000c1056000) (0MB)
[    0.000000] efi: mem110: type=4, attr=0xf, range=[0x00000000c1056000-0x00000000c1072000) (0MB)
[    0.000000] efi: mem111: type=7, attr=0xf, range=[0x00000000c1072000-0x00000000c107c000) (0MB)
[    0.000000] efi: mem112: type=4, attr=0xf, range=[0x00000000c107c000-0x00000000c13b9000) (3MB)
[    0.000000] efi: mem113: type=7, attr=0xf, range=[0x00000000c13b9000-0x00000000c13c5000) (0MB)
[    0.000000] efi: mem114: type=4, attr=0xf, range=[0x00000000c13c5000-0x00000000c13cf000) (0MB)
[    0.000000] efi: mem115: type=7, attr=0xf, range=[0x00000000c13cf000-0x00000000c13f0000) (0MB)
[    0.000000] efi: mem116: type=4, attr=0xf, range=[0x00000000c13f0000-0x00000000c13fb000) (0MB)
[    0.000000] efi: mem117: type=7, attr=0xf, range=[0x00000000c13fb000-0x00000000c1404000) (0MB)
[    0.000000] efi: mem118: type=4, attr=0xf, range=[0x00000000c1404000-0x00000000c166f000) (2MB)
[    0.000000] efi: mem119: type=7, attr=0xf, range=[0x00000000c166f000-0x00000000c1671000) (0MB)
[    0.000000] efi: mem120: type=4, attr=0xf, range=[0x00000000c1671000-0x00000000c1675000) (0MB)
[    0.000000] efi: mem121: type=7, attr=0xf, range=[0x00000000c1675000-0x00000000c1677000) (0MB)
[    0.000000] efi: mem122: type=4, attr=0xf, range=[0x00000000c1677000-0x00000000c167e000) (0MB)
[    0.000000] efi: mem123: type=7, attr=0xf, range=[0x00000000c167e000-0x00000000c1681000) (0MB)
[    0.000000] efi: mem124: type=4, attr=0xf, range=[0x00000000c1681000-0x00000000c1686000) (0MB)
[    0.000000] efi: mem125: type=7, attr=0xf, range=[0x00000000c1686000-0x00000000c1688000) (0MB)
[    0.000000] efi: mem126: type=4, attr=0xf, range=[0x00000000c1688000-0x00000000c168b000) (0MB)
[    0.000000] efi: mem127: type=7, attr=0xf, range=[0x00000000c168b000-0x00000000c168d000) (0MB)
[    0.000000] efi: mem128: type=4, attr=0xf, range=[0x00000000c168d000-0x00000000c16aa000) (0MB)
[    0.000000] efi: mem129: type=7, attr=0xf, range=[0x00000000c16aa000-0x00000000c16b0000) (0MB)
[    0.000000] efi: mem130: type=4, attr=0xf, range=[0x00000000c16b0000-0x00000000c1796000) (0MB)
[    0.000000] efi: mem131: type=7, attr=0xf, range=[0x00000000c1796000-0x00000000c17a2000) (0MB)
[    0.000000] efi: mem132: type=4, attr=0xf, range=[0x00000000c17a2000-0x00000000c1807000) (0MB)
[    0.000000] efi: mem133: type=7, attr=0xf, range=[0x00000000c1807000-0x00000000c1808000) (0MB)
[    0.000000] efi: mem134: type=4, attr=0xf, range=[0x00000000c1808000-0x00000000c1816000) (0MB)
[    0.000000] efi: mem135: type=7, attr=0xf, range=[0x00000000c1816000-0x00000000c1817000) (0MB)
[    0.000000] efi: mem136: type=4, attr=0xf, range=[0x00000000c1817000-0x00000000c182b000) (0MB)
[    0.000000] efi: mem137: type=7, attr=0xf, range=[0x00000000c182b000-0x00000000c182c000) (0MB)
[    0.000000] efi: mem138: type=4, attr=0xf, range=[0x00000000c182c000-0x00000000c183a000) (0MB)
[    0.000000] efi: mem139: type=7, attr=0xf, range=[0x00000000c183a000-0x00000000c183b000) (0MB)
[    0.000000] efi: mem140: type=4, attr=0xf, range=[0x00000000c183b000-0x00000000c1873000) (0MB)
[    0.000000] efi: mem141: type=7, attr=0xf, range=[0x00000000c1873000-0x00000000c1874000) (0MB)
[    0.000000] efi: mem142: type=4, attr=0xf, range=[0x00000000c1874000-0x00000000cafce000) (151MB)
[    0.000000] efi: mem143: type=7, attr=0xf, range=[0x00000000cafce000-0x00000000cafd0000) (0MB)
[    0.000000] efi: mem144: type=4, attr=0xf, range=[0x00000000cafd0000-0x00000000ccb02000) (27MB)
[    0.000000] efi: mem145: type=7, attr=0xf, range=[0x00000000ccb02000-0x00000000cd60e000) (11MB)
[    0.000000] efi: mem146: type=2, attr=0xf, range=[0x00000000cd60e000-0x00000000cd612000) (0MB)
[    0.000000] efi: mem147: type=3, attr=0xf, range=[0x00000000cd612000-0x00000000cd892000) (2MB)
[    0.000000] efi: mem148: type=0, attr=0xf, range=[0x00000000cd892000-0x00000000cd901000) (0MB)
[    0.000000] efi: mem149: type=0, attr=0xf, range=[0x00000000cd901000-0x00000000cdac0000) (1MB)
[    0.000000] efi: mem150: type=9, attr=0xf, range=[0x00000000cdac0000-0x00000000cdac1000) (0MB)
[    0.000000] efi: mem151: type=10, attr=0xf, range=[0x00000000cdac1000-0x00000000cdb0c000) (0MB)
[    0.000000] efi: mem152: type=10, attr=0xf, range=[0x00000000cdb0c000-0x00000000cdb1f000) (0MB)
[    0.000000] efi: mem153: type=10, attr=0xf, range=[0x00000000cdb1f000-0x00000000cdb44000) (0MB)
[    0.000000] efi: mem154: type=10, attr=0xf, range=[0x00000000cdb44000-0x00000000cdbc8000) (0MB)
[    0.000000] efi: mem155: type=10, attr=0xf, range=[0x00000000cdbc8000-0x00000000cdbd2000) (0MB)
[    0.000000] efi: mem156: type=10, attr=0xf, range=[0x00000000cdbd2000-0x00000000cdbe4000) (0MB)
[    0.000000] efi: mem157: type=10, attr=0xf, range=[0x00000000cdbe4000-0x00000000cdbea000) (0MB)
[    0.000000] efi: mem158: type=10, attr=0xf, range=[0x00000000cdbea000-0x00000000cdbf2000) (0MB)
[    0.000000] efi: mem159: type=6, attr=0x800000000000000f, range=[0x00000000cdbf2000-0x00000000ce211000) (6MB)
[    0.000000] efi: mem160: type=6, attr=0x800000000000000f, range=[0x00000000ce211000-0x00000000ce92d000) (7MB)
[    0.000000] efi: mem161: type=6, attr=0x800000000000000f, range=[0x00000000ce92d000-0x00000000ce92f000) (0MB)
[    0.000000] efi: mem162: type=6, attr=0x800000000000000f, range=[0x00000000ce92f000-0x00000000ce93c000) (0MB)
[    0.000000] efi: mem163: type=6, attr=0x800000000000000f, range=[0x00000000ce93c000-0x00000000ce93e000) (0MB)
[    0.000000] efi: mem164: type=6, attr=0x800000000000000f, range=[0x00000000ce93e000-0x00000000ce9dc000) (0MB)
[    0.000000] efi: mem165: type=5, attr=0x800000000000000f, range=[0x00000000ce9dc000-0x00000000cea01000) (0MB)
[    0.000000] efi: mem166: type=5, attr=0x800000000000000f, range=[0x00000000cea01000-0x00000000cea95000) (0MB)
[    0.000000] efi: mem167: type=4, attr=0xf, range=[0x00000000cea95000-0x00000000cea96000) (0MB)
[    0.000000] efi: mem168: type=10, attr=0xf, range=[0x00000000cea96000-0x00000000cead9000) (0MB)
[    0.000000] efi: mem169: type=4, attr=0xf, range=[0x00000000cead9000-0x00000000cec4d000) (1MB)
[    0.000000] efi: mem170: type=3, attr=0xf, range=[0x00000000cec4d000-0x00000000cf44a000) (7MB)
[    0.000000] efi: mem171: type=4, attr=0xf, range=[0x00000000cf44a000-0x00000000cf44d000) (0MB)
[    0.000000] efi: mem172: type=3, attr=0xf, range=[0x00000000cf44d000-0x00000000cf44f000) (0MB)
[    0.000000] efi: mem173: type=4, attr=0xf, range=[0x00000000cf44f000-0x00000000cf45c000) (0MB)
[    0.000000] efi: mem174: type=3, attr=0xf, range=[0x00000000cf45c000-0x00000000cf46e000) (0MB)
[    0.000000] efi: mem175: type=4, attr=0xf, range=[0x00000000cf46e000-0x00000000cf46f000) (0MB)
[    0.000000] efi: mem176: type=3, attr=0xf, range=[0x00000000cf46f000-0x00000000cf471000) (0MB)
[    0.000000] efi: mem177: type=4, attr=0xf, range=[0x00000000cf471000-0x00000000cf479000) (0MB)
[    0.000000] efi: mem178: type=6, attr=0x800000000000000f, range=[0x00000000cf479000-0x00000000cf7d7000) (3MB)
[    0.000000] efi: mem179: type=4, attr=0xf, range=[0x00000000cf7d7000-0x00000000cf800000) (0MB)
[    0.000000] efi: mem180: type=7, attr=0xf, range=[0x0000000100000000-0x000000042f000000) (13040MB)
[    0.000000] efi: mem181: type=11, attr=0x8000000000000001, range=[0x00000000f0000000-0x00000000f8000000) (128MB)
[    0.000000] efi: mem182: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem183: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed04000) (0MB)
[    0.000000] efi: mem184: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem185: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem186: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. To be filled by O.E.M./Z77X-UP5 TH-CF, BIOS F11 09/03/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x42f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 400000000 mask FE0000000 write-back
[    0.000000]   2 base 420000000 mask FF8000000 write-back
[    0.000000]   3 base 428000000 mask FFC000000 write-back
[    0.000000]   4 base 42C000000 mask FFE000000 write-back
[    0.000000]   5 base 42E000000 mask FFF000000 write-back
[    0.000000]   6 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   7 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 512MB, type WB
[    0.000000] reg 2, base: 16896MB, range: 128MB, type WB
[    0.000000] reg 3, base: 17024MB, range: 64MB, type WB
[    0.000000] reg 4, base: 17088MB, range: 32MB, type WB
[    0.000000] reg 5, base: 17120MB, range: 16MB, type WB
[    0.000000] reg 6, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 7, base: 3328MB, range: 256MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 512MB, type WB
[    0.000000] reg 6, base: 16896MB, range: 256MB, type WB
[    0.000000] reg 7, base: 17136MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xd0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcf800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd7e0-0x000fd7ef] mapped at [ffff8800000fd7e0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd9000, 0x01fd9fff] PGTABLE
[    0.000000] BRK [0x01fda000, 0x01fdafff] PGTABLE
[    0.000000] BRK [0x01fdb000, 0x01fdbfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42ee00000-0x42effffff]
[    0.000000]  [mem 0x42ee00000-0x42effffff] page 2M
[    0.000000] BRK [0x01fdc000, 0x01fdcfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x42c000000-0x42edfffff]
[    0.000000]  [mem 0x42c000000-0x42edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x42bffffff]
[    0.000000]  [mem 0x400000000-0x42bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xcd891fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xcd7fffff] page 2M
[    0.000000]  [mem 0xcd800000-0xcd891fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xcea95000-0xcea95fff]
[    0.000000]  [mem 0xcea95000-0xcea95fff] page 4k
[    0.000000] BRK [0x01fdd000, 0x01fddfff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xcead9000-0xcf478fff]
[    0.000000]  [mem 0xcead9000-0xcebfffff] page 4k
[    0.000000]  [mem 0xcec00000-0xcf3fffff] page 2M
[    0.000000]  [mem 0xcf400000-0xcf478fff] page 4k
[    0.000000] BRK [0x01fde000, 0x01fdefff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xcf7d7000-0xcf7fffff]
[    0.000000]  [mem 0xcf7d7000-0xcf7fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x3ffffffff]
[    0.000000]  [mem 0x100000000-0x3ffffffff] page 2M
[    0.000000] RAMDISK: [mem 0x35c88000-0x36e3bfff]
[    0.000000] ACPI: RSDP 00000000cdbd2000 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000cdbd2070 00064 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000cdbdc850 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000cdbd2170 0A6DF (v02 ALASKA    A M I 00000012 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cdbf0f80 00040
[    0.000000] ACPI: APIC 00000000cdbdc948 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000cdbdc9c0 0003C (v01                 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cdbdca00 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000cdbdca38 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000cdbdcda8 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cdbdd758 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: MATS 00000000cdbde1f0 00034 (v02 ALASKA    A M I 00000002 w?x2 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000042effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x42effffff]
[    0.000000]   NODE_DATA [mem 0x42efea000-0x42efeefff]
[    0.000000]  [ffffea0000000000-ffffea0010bfffff] PMD -> [ffff88041e600000-ffff88042e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x42effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xcd891fff]
[    0.000000]   node   0: [mem 0xcea95000-0xcea95fff]
[    0.000000]   node   0: [mem 0xcead9000-0xcf478fff]
[    0.000000]   node   0: [mem 0xcf7d7000-0xcf7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x42effffff]
[    0.000000] On node 0 totalpages: 4182522
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 25 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13130 pages used for memmap
[    0.000000]   DMA32 zone: 840284 pages, LIFO batch:31
[    0.000000]   Normal zone: 52160 pages used for memmap
[    0.000000]   Normal zone: 3338240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcd892000-0xcdabffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcdac0000-0xcdac0fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcdac1000-0xcdbf1fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcdbf2000-0xcea94fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcea96000-0xcead8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcf479000-0xcf7d6fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcf800000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xcf800000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88042ec00000 s86720 r8192 d23872 u524288
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4117143
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16152276K/16730088K available (7507K kernel code, 1079K rwdata, 4076K rodata, 1392K init, 1428K bss, 577812K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3403.416 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6806.83 BogoMIPS (lpj=13613664)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000018] init_memory_mapping: [mem 0xcdbf2000-0xce9dbfff]
[    0.000020]  [mem 0xcdbf2000-0xcdbfffff] page 4k
[    0.000020]  [mem 0xcdc00000-0xce7fffff] page 2M
[    0.000021]  [mem 0xce800000-0xce9dbfff] page 4k
[    0.000039] init_memory_mapping: [mem 0xce9dc000-0xcea94fff]
[    0.000040]  [mem 0xce9dc000-0xcea94fff] page 4k
[    0.000047] init_memory_mapping: [mem 0xcf479000-0xcf7d6fff]
[    0.000048]  [mem 0xcf479000-0xcf7d6fff] page 4k
[    0.009683] Security Framework initialized
[    0.009694] AppArmor: AppArmor initialized
[    0.009695] Yama: becoming mindful.
[    0.010345] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.013218] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.014489] Mount-cache hash table entries: 256
[    0.014610] Initializing cgroup subsys memory
[    0.014616] Initializing cgroup subsys devices
[    0.014617] Initializing cgroup subsys freezer
[    0.014618] Initializing cgroup subsys blkio
[    0.014619] Initializing cgroup subsys perf_event
[    0.014620] Initializing cgroup subsys hugetlb
[    0.014637] CPU: Physical Processor ID: 0
[    0.014638] CPU: Processor Core ID: 0
[    0.014641] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.014641] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.014902] mce: CPU supports 9 MCE banks
[    0.014912] CPU0: Thermal monitoring enabled (TM1)
[    0.014921] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.014921] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.014921] tlb_flushall_shift: 1
[    0.015010] Freeing SMP alternatives memory: 28K (ffffffff81e6b000 - ffffffff81e72000)
[    0.016554] ACPI: Core revision 20130517
[    0.020253] ACPI: All ACPI Tables successfully acquired
[    0.027338] ftrace: allocating 31294 entries in 123 pages
[    0.038279] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.077979] smpboot: CPU0: Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz (fam: 06, model: 3a, stepping: 09)
[    0.077985] TSC deadline timer enabled
[    0.077991] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.077997] ... version:                3
[    0.077997] ... bit width:              48
[    0.077998] ... generic registers:      8
[    0.077998] ... value mask:             0000ffffffffffff
[    0.077999] ... max period:             0000ffffffffffff
[    0.078000] ... fixed-purpose events:   3
[    0.078000] ... event mask:             00000007000000ff
[    0.092357] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.079079] smpboot: Booting Node   0, Processors  #1 #2 #3 OK
[    0.119175] Brought up 4 CPUs
[    0.119179] smpboot: Total of 4 processors activated (27227.32 BogoMIPS)
[    0.121811] devtmpfs: initialized
[    0.122902] EVM: security.selinux
[    0.122903] EVM: security.SMACK64
[    0.122904] EVM: security.capability
[    0.122933] PM: Registering ACPI NVS region [mem 0xcdac1000-0xcdbf1fff] (1249280 bytes)
[    0.122945] PM: Registering ACPI NVS region [mem 0xcea96000-0xcead8fff] (274432 bytes)
[    0.123484] regulator-dummy: no parameters
[    0.123511] RTC time:  8:39:25, date: 02/10/14
[    0.123535] NET: Registered protocol family 16
[    0.123624] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.123626] ACPI: bus type PCI registered
[    0.123627] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.123662] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.123664] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.131797] PCI: Using configuration type 1 for base access
[    0.132434] bio: create slab <bio-0> at 0
[    0.132528] ACPI: Added _OSI(Module Device)
[    0.132529] ACPI: Added _OSI(Processor Device)
[    0.132530] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.132531] ACPI: Added _OSI(Processor Aggregator Device)
[    0.133533] ACPI: EC: Look up EC in DSDT
[    0.134589] ACPI: Executed 1 blocks of module-level executable AML code
[    0.141944] ACPI: SSDT 00000000cda62018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.142194] ACPI: Dynamic OEM Table Load:
[    0.142195] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.145839] ACPI: SSDT 00000000cda63a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.146106] ACPI: Dynamic OEM Table Load:
[    0.146107] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.149757] ACPI: SSDT 00000000cda6fc18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.150003] ACPI: Dynamic OEM Table Load:
[    0.150004] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.154063] ACPI: Interpreter enabled
[    0.154068] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.154070] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.154079] ACPI: (supports S0 S3 S4 S5)
[    0.154080] ACPI: Using IOAPIC for interrupt routing
[    0.154098] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.154185] ACPI: No dock devices found.
[    0.158600] ACPI: Power Resource [FN00] (off)
[    0.158651] ACPI: Power Resource [FN01] (off)
[    0.158702] ACPI: Power Resource [FN02] (off)
[    0.158751] ACPI: Power Resource [FN03] (off)
[    0.158799] ACPI: Power Resource [FN04] (off)
[    0.159204] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    0.159345] acpi PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.159474] acpi PNP0A08:00: ACPI _OSC control (0x18) granted
[    0.159853] PCI host bridge to bus 0000:00
[    0.159855] pci_bus 0000:00: root bus resource [bus 00-7e]
[    0.159856] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.159857] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.159858] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.159860] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.159861] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.159862] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.159863] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.159864] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xfeafffff]
[    0.159870] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
[    0.159933] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.159955] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.159988] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.160032] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.160053] pci 0000:00:14.0: reg 0x10: [mem 0xef520000-0xef52ffff 64bit]
[    0.160118] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.160155] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.160179] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.160200] pci 0000:00:16.0: reg 0x10: [mem 0xef53b000-0xef53b00f 64bit]
[    0.160269] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.160331] pci 0000:00:19.0: [8086:1503] type 00 class 0x020000
[    0.160347] pci 0000:00:19.0: reg 0x10: [mem 0xef500000-0xef51ffff]
[    0.160354] pci 0000:00:19.0: reg 0x14: [mem 0xef539000-0xef539fff]
[    0.160361] pci 0000:00:19.0: reg 0x18: [io  0xf040-0xf05f]
[    0.160418] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.160455] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.160480] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.160499] pci 0000:00:1a.0: reg 0x10: [mem 0xef538000-0xef5383ff]
[    0.160582] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.160628] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.160652] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.160666] pci 0000:00:1b.0: reg 0x10: [mem 0xef530000-0xef533fff 64bit]
[    0.160727] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.160764] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.160786] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.160857] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.160896] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.160920] pci 0000:00:1c.4: [8086:1e18] type 01 class 0x060400
[    0.160991] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.161031] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.161052] pci 0000:00:1c.5: [8086:244e] type 01 class 0x060401
[    0.161122] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.161162] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.161185] pci 0000:00:1c.7: [8086:1e1e] type 01 class 0x060400
[    0.161255] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.161295] pci 0000:00:1c.7: System wakeup disabled by ACPI
[    0.161320] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.161338] pci 0000:00:1d.0: reg 0x10: [mem 0xef537000-0xef5373ff]
[    0.161421] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.161467] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.161492] pci 0000:00:1f.0: [8086:1e44] type 00 class 0x060100
[    0.161641] pci 0000:00:1f.2: [8086:1e02] type 00 class 0x010601
[    0.161657] pci 0000:00:1f.2: reg 0x10: [io  0xf090-0xf097]
[    0.161663] pci 0000:00:1f.2: reg 0x14: [io  0xf080-0xf083]
[    0.161669] pci 0000:00:1f.2: reg 0x18: [io  0xf070-0xf077]
[    0.161676] pci 0000:00:1f.2: reg 0x1c: [io  0xf060-0xf063]
[    0.161682] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.161689] pci 0000:00:1f.2: reg 0x24: [mem 0xef536000-0xef5367ff]
[    0.161728] pci 0000:00:1f.2: PME# supported from D3hot
[    0.161779] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.161792] pci 0000:00:1f.3: reg 0x10: [mem 0xef535000-0xef5350ff 64bit]
[    0.161810] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.162356] pci 0000:01:00.0: [10de:1183] type 00 class 0x030000
[    0.162364] pci 0000:01:00.0: reg 0x10: [mem 0xe6000000-0xe6ffffff]
[    0.162373] pci 0000:01:00.0: reg 0x14: [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.162381] pci 0000:01:00.0: reg 0x1c: [mem 0xd8000000-0xd9ffffff 64bit pref]
[    0.162387] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.162393] pci 0000:01:00.0: reg 0x30: [mem 0xe7000000-0xe707ffff pref]
[    0.162450] pci 0000:01:00.1: [10de:0e0a] type 00 class 0x040300
[    0.162458] pci 0000:01:00.1: reg 0x10: [mem 0xe7080000-0xe7083fff]
[    0.167225] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.167229] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.167232] pci 0000:00:01.0:   bridge window [mem 0xe6000000-0xe70fffff]
[    0.167237] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.167319] acpiphp: Slot [1] registered
[    0.167323] pci 0000:00:1c.0: PCI bridge to [bus 02-62]
[    0.167326] pci 0000:00:1c.0:   bridge window [io  0x7000-0xbfff]
[    0.167329] pci 0000:00:1c.0:   bridge window [mem 0xe7100000-0xef0fffff]
[    0.167334] pci 0000:00:1c.0:   bridge window [mem 0xda100000-0xe20fffff 64bit pref]
[    0.167411] pci 0000:63:00.0: [10b5:8605] type 01 class 0x060400
[    0.167553] pci 0000:63:00.0: supports D1 D2
[    0.167554] pci 0000:63:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.175232] pci 0000:00:1c.4: PCI bridge to [bus 63-67]
[    0.175240] pci 0000:00:1c.4:   bridge window [mem 0xef100000-0xef2fffff]
[    0.175378] pci 0000:64:01.0: [10b5:8605] type 01 class 0x060400
[    0.175523] pci 0000:64:01.0: supports D1 D2
[    0.175524] pci 0000:64:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.175596] pci 0000:64:02.0: [10b5:8605] type 01 class 0x060400
[    0.175740] pci 0000:64:02.0: supports D1 D2
[    0.175741] pci 0000:64:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.175812] pci 0000:64:03.0: [10b5:8605] type 01 class 0x060400
[    0.175957] pci 0000:64:03.0: supports D1 D2
[    0.175957] pci 0000:64:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176056] pci 0000:63:00.0: PCI bridge to [bus 64-67]
[    0.176069] pci 0000:63:00.0:   bridge window [mem 0xef100000-0xef1fffff]
[    0.176167] pci 0000:64:01.0: PCI bridge to [bus 65]
[    0.176278] pci 0000:64:02.0: PCI bridge to [bus 66]
[    0.176420] pci 0000:67:00.0: [168c:0030] type 00 class 0x028000
[    0.176457] pci 0000:67:00.0: reg 0x10: [mem 0xef100000-0xef11ffff 64bit]
[    0.176549] pci 0000:67:00.0: reg 0x30: [mem 0xef120000-0xef12ffff pref]
[    0.176644] pci 0000:67:00.0: supports D1
[    0.176645] pci 0000:67:00.0: PME# supported from D0 D1 D3hot
[    0.183248] pci 0000:64:03.0: PCI bridge to [bus 67]
[    0.183264] pci 0000:64:03.0:   bridge window [mem 0xef100000-0xef1fffff]
[    0.183387] pci 0000:68:00.0: [8086:244e] type 01 class 0x060401
[    0.183535] pci 0000:68:00.0: supports D1 D2
[    0.183536] pci 0000:68:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183560] pci 0000:68:00.0: System wakeup disabled by ACPI
[    0.183576] pci 0000:00:1c.5: PCI bridge to [bus 68-69] (subtractive decode)
[    0.183579] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.183582] pci 0000:00:1c.5:   bridge window [mem 0xef400000-0xef4fffff]
[    0.183587] pci 0000:00:1c.5:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.183588] pci 0000:00:1c.5:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.183589] pci 0000:00:1c.5:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.183590] pci 0000:00:1c.5:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.183591] pci 0000:00:1c.5:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.183593] pci 0000:00:1c.5:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.183594] pci 0000:00:1c.5:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.183595] pci 0000:00:1c.5:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    0.183685] pci 0000:69:01.0: [1106:3044] type 00 class 0x0c0010
[    0.183719] pci 0000:69:01.0: reg 0x10: [mem 0xef400000-0xef4007ff]
[    0.183738] pci 0000:69:01.0: reg 0x14: [io  0xd000-0xd07f]
[    0.183884] pci 0000:69:01.0: supports D2
[    0.183885] pci 0000:69:01.0: PME# supported from D2 D3hot D3cold
[    0.183989] pci 0000:68:00.0: PCI bridge to [bus 69] (subtractive decode)
[    0.184000] pci 0000:68:00.0:   bridge window [io  0xd000-0xdfff]
[    0.184005] pci 0000:68:00.0:   bridge window [mem 0xef400000-0xef4fffff]
[    0.184015] pci 0000:68:00.0:   bridge window [io  0xd000-0xdfff] (subtractive decode)
[    0.184016] pci 0000:68:00.0:   bridge window [mem 0xef400000-0xef4fffff] (subtractive decode)
[    0.184018] pci 0000:68:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.184019] pci 0000:68:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.184020] pci 0000:68:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.184021] pci 0000:68:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.184022] pci 0000:68:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.184023] pci 0000:68:00.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.184024] pci 0000:68:00.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.184025] pci 0000:68:00.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.184026] pci 0000:68:00.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.184028] pci 0000:68:00.0:   bridge window [mem 0xd0000000-0xfeafffff] (subtractive decode)
[    0.184107] pci 0000:6a:00.0: [1b4b:9172] type 00 class 0x010601
[    0.184124] pci 0000:6a:00.0: reg 0x10: [io  0xc040-0xc047]
[    0.184135] pci 0000:6a:00.0: reg 0x14: [io  0xc030-0xc033]
[    0.184147] pci 0000:6a:00.0: reg 0x18: [io  0xc020-0xc027]
[    0.184158] pci 0000:6a:00.0: reg 0x1c: [io  0xc010-0xc013]
[    0.184170] pci 0000:6a:00.0: reg 0x20: [io  0xc000-0xc00f]
[    0.184181] pci 0000:6a:00.0: reg 0x24: [mem 0xef310000-0xef3101ff]
[    0.184193] pci 0000:6a:00.0: reg 0x30: [mem 0xef300000-0xef30ffff pref]
[    0.184248] pci 0000:6a:00.0: PME# supported from D3hot
[    0.184270] pci 0000:6a:00.0: System wakeup disabled by ACPI
[    0.191248] pci 0000:00:1c.7: PCI bridge to [bus 6a]
[    0.191253] pci 0000:00:1c.7:   bridge window [io  0xc000-0xcfff]
[    0.191258] pci 0000:00:1c.7:   bridge window [mem 0xef300000-0xef3fffff]
[    0.191297] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.191627] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.191663] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.191697] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.191731] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.191764] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.191798] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.191832] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.191866] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.192019] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.192023] ACPI: \_SB_.PCI0: notify handler is installed
[    0.192062] Found 1 acpi root devices
[    0.192123] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.192124] vgaarb: loaded
[    0.192125] vgaarb: bridge control possible 0000:01:00.0
[    0.192221] SCSI subsystem initialized
[    0.192222] ACPI: bus type ATA registered
[    0.192243] libata version 3.00 loaded.
[    0.192251] ACPI: bus type USB registered
[    0.192262] usbcore: registered new interface driver usbfs
[    0.192266] usbcore: registered new interface driver hub
[    0.192277] usbcore: registered new device driver usb
[    0.192336] PCI: Using ACPI for IRQ routing
[    0.195653] PCI: pci_cache_line_size set to 64 bytes
[    0.195724] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.195726] e820: reserve RAM buffer [mem 0xcd892000-0xcfffffff]
[    0.195727] e820: reserve RAM buffer [mem 0xcea96000-0xcfffffff]
[    0.195728] e820: reserve RAM buffer [mem 0xcf479000-0xcfffffff]
[    0.195729] e820: reserve RAM buffer [mem 0xcf800000-0xcfffffff]
[    0.195730] e820: reserve RAM buffer [mem 0x42f000000-0x42fffffff]
[    0.195780] NetLabel: Initializing
[    0.195781] NetLabel:  domain hash size = 128
[    0.195782] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.195787] NetLabel:  unlabeled traffic allowed by default
[    0.195821] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.195824] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.197839] Switched to clocksource hpet
[    0.200755] AppArmor: AppArmor Filesystem Enabled
[    0.200771] pnp: PnP ACPI init
[    0.200777] ACPI: bus type PNP registered
[    0.200824] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.200827] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.200834] pnp 00:01: [dma 4]
[    0.200844] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.200855] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.200912] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.200940] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.200941] system 00:04: [io  0x0200-0x020f] has been reserved
[    0.200943] system 00:04: [io  0xffff] has been reserved
[    0.200944] system 00:04: [io  0xffff] has been reserved
[    0.200945] system 00:04: [io  0x0400-0x0453] could not be reserved
[    0.200947] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.200948] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.200949] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.200966] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.200996] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.200998] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.201074] system 00:07: [io  0x0a00-0x0a0f] has been reserved
[    0.201075] system 00:07: [io  0x0a30-0x0a3f] has been reserved
[    0.201076] system 00:07: [io  0x0a20-0x0a2f] has been reserved
[    0.201078] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.201123] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.201124] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.201139] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.201306] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.201308] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.201309] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.201311] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.201312] system 00:0a: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.201313] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.201314] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.201316] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.201318] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
[    0.201319] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.201320] system 00:0a: [mem 0xe2100000-0xe2100fff] has been reserved
[    0.201322] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.201405] pnp: PnP ACPI: found 11 devices
[    0.201406] ACPI: bus type PNP unregistered
[    0.207178] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.207180] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.207182] pci 0000:00:01.0:   bridge window [mem 0xe6000000-0xe70fffff]
[    0.207184] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.207187] pci 0000:00:1c.0: PCI bridge to [bus 02-62]
[    0.207189] pci 0000:00:1c.0:   bridge window [io  0x7000-0xbfff]
[    0.207193] pci 0000:00:1c.0:   bridge window [mem 0xe7100000-0xef0fffff]
[    0.207196] pci 0000:00:1c.0:   bridge window [mem 0xda100000-0xe20fffff 64bit pref]
[    0.207201] pci 0000:64:01.0: PCI bridge to [bus 65]
[    0.207219] pci 0000:64:02.0: PCI bridge to [bus 66]
[    0.207238] pci 0000:64:03.0: PCI bridge to [bus 67]
[    0.207245] pci 0000:64:03.0:   bridge window [mem 0xef100000-0xef1fffff]
[    0.207258] pci 0000:63:00.0: PCI bridge to [bus 64-67]
[    0.207265] pci 0000:63:00.0:   bridge window [mem 0xef100000-0xef1fffff]
[    0.207277] pci 0000:00:1c.4: PCI bridge to [bus 63-67]
[    0.207281] pci 0000:00:1c.4:   bridge window [mem 0xef100000-0xef2fffff]
[    0.207288] pci 0000:68:00.0: PCI bridge to [bus 69]
[    0.207292] pci 0000:68:00.0:   bridge window [io  0xd000-0xdfff]
[    0.207299] pci 0000:68:00.0:   bridge window [mem 0xef400000-0xef4fffff]
[    0.207314] pci 0000:00:1c.5: PCI bridge to [bus 68-69]
[    0.207316] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.207320] pci 0000:00:1c.5:   bridge window [mem 0xef400000-0xef4fffff]
[    0.207327] pci 0000:00:1c.7: PCI bridge to [bus 6a]
[    0.207329] pci 0000:00:1c.7:   bridge window [io  0xc000-0xcfff]
[    0.207333] pci 0000:00:1c.7:   bridge window [mem 0xef300000-0xef3fffff]
[    0.207624] pci 0000:68:00.0: setting latency timer to 64
[    0.207671] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.207672] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.207673] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.207675] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.207676] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.207677] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.207678] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.207679] pci_bus 0000:00: resource 11 [mem 0xd0000000-0xfeafffff]
[    0.207680] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.207681] pci_bus 0000:01: resource 1 [mem 0xe6000000-0xe70fffff]
[    0.207682] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd9ffffff 64bit pref]
[    0.207684] pci_bus 0000:02: resource 0 [io  0x7000-0xbfff]
[    0.207685] pci_bus 0000:02: resource 1 [mem 0xe7100000-0xef0fffff]
[    0.207686] pci_bus 0000:02: resource 2 [mem 0xda100000-0xe20fffff 64bit pref]
[    0.207687] pci_bus 0000:63: resource 1 [mem 0xef100000-0xef2fffff]
[    0.207689] pci_bus 0000:64: resource 1 [mem 0xef100000-0xef1fffff]
[    0.207690] pci_bus 0000:67: resource 1 [mem 0xef100000-0xef1fffff]
[    0.207691] pci_bus 0000:68: resource 0 [io  0xd000-0xdfff]
[    0.207692] pci_bus 0000:68: resource 1 [mem 0xef400000-0xef4fffff]
[    0.207693] pci_bus 0000:68: resource 4 [io  0x0000-0x0cf7]
[    0.207694] pci_bus 0000:68: resource 5 [io  0x0d00-0xffff]
[    0.207695] pci_bus 0000:68: resource 6 [mem 0x000a0000-0x000bffff]
[    0.207696] pci_bus 0000:68: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.207698] pci_bus 0000:68: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.207699] pci_bus 0000:68: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.207700] pci_bus 0000:68: resource 10 [mem 0x000dc000-0x000dffff]
[    0.207701] pci_bus 0000:68: resource 11 [mem 0xd0000000-0xfeafffff]
[    0.207702] pci_bus 0000:69: resource 0 [io  0xd000-0xdfff]
[    0.207703] pci_bus 0000:69: resource 1 [mem 0xef400000-0xef4fffff]
[    0.207704] pci_bus 0000:69: resource 4 [io  0xd000-0xdfff]
[    0.207705] pci_bus 0000:69: resource 5 [mem 0xef400000-0xef4fffff]
[    0.207706] pci_bus 0000:69: resource 8 [io  0x0000-0x0cf7]
[    0.207708] pci_bus 0000:69: resource 9 [io  0x0d00-0xffff]
[    0.207709] pci_bus 0000:69: resource 10 [mem 0x000a0000-0x000bffff]
[    0.207710] pci_bus 0000:69: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.207711] pci_bus 0000:69: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.207712] pci_bus 0000:69: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.207713] pci_bus 0000:69: resource 14 [mem 0x000dc000-0x000dffff]
[    0.207714] pci_bus 0000:69: resource 15 [mem 0xd0000000-0xfeafffff]
[    0.207716] pci_bus 0000:6a: resource 0 [io  0xc000-0xcfff]
[    0.207717] pci_bus 0000:6a: resource 1 [mem 0xef300000-0xef3fffff]
[    0.207734] NET: Registered protocol family 2
[    0.207889] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.208143] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.208251] TCP: Hash tables configured (established 131072 bind 65536)
[    0.208262] TCP: reno registered
[    0.208274] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.208314] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.208375] NET: Registered protocol family 1
[    0.245964] pci 0000:01:00.0: Boot video device
[    0.245992] PCI: CLS 64 bytes, default 64
[    0.246021] Trying to unpack rootfs image as initramfs...
[    2.721632] Freeing initrd memory: 18128K (ffff880035c88000 - ffff880036e3c000)
[    2.721636] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.721638] software IO TLB [mem 0xbbcef000-0xbfcef000] (64MB) mapped at [ffff8800bbcef000-ffff8800bfceefff]
[    2.721781] Scanning for low memory corruption every 60 seconds
[    2.721947] Initialise module verification
[    2.721973] audit: initializing netlink socket (disabled)
[    2.721981] type=2000 audit(1392021567.712:1): initialized
[    2.741486] bounce pool size: 64 pages
[    2.741492] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.742434] zbud: loaded
[    2.742517] VFS: Disk quotas dquot_6.5.2
[    2.742540] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.742816] fuse init (API version 7.22)
[    2.742869] msgmni has been set to 32001
[    2.743222] Key type asymmetric registered
[    2.743223] Asymmetric key parser 'x509' registered
[    2.743240] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    2.743266] io scheduler noop registered
[    2.743267] io scheduler deadline registered (default)
[    2.743280] io scheduler cfq registered
[    2.743344] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    2.743514] pcieport 0000:63:00.0: irq 41 for MSI/MSI-X
[    2.743636] pcieport 0000:64:01.0: irq 42 for MSI/MSI-X
[    2.743759] pcieport 0000:64:02.0: irq 43 for MSI/MSI-X
[    2.743880] pcieport 0000:64:03.0: irq 44 for MSI/MSI-X
[    2.743974] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.743983] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.744030] efifb: probing for efifb
[    2.744170] efifb: framebuffer at 0xd9000000, mapped to 0xffffc90012d00000, using 1920k, total 1920k
[    2.744171] efifb: mode is 800x600x32, linelength=3200, pages=1
[    2.744171] efifb: scrolling: redraw
[    2.744172] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.744899] Console: switching to colour frame buffer device 100x37
[    2.745567] fb0: EFI VGA frame buffer device
[    2.745571] intel_idle: MWAIT substates: 0x1120
[    2.745572] intel_idle: v0.4 model 0x3A
[    2.745573] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.745640] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    2.745643] ACPI: Power Button [PWRB]
[    2.745663] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    2.745665] ACPI: Power Button [PWRF]
[    2.745715] ACPI: Fan [FAN0] (off)
[    2.745734] ACPI: Fan [FAN1] (off)
[    2.745749] ACPI: Fan [FAN2] (off)
[    2.745763] ACPI: Fan [FAN3] (off)
[    2.745778] ACPI: Fan [FAN4] (off)
[    2.745810] ACPI: Requesting acpi_cpufreq
[    2.759168] thermal LNXTHERM:00: registered as thermal_zone0
[    2.759170] ACPI: Thermal Zone [TZ00] (28 C)
[    2.759313] thermal LNXTHERM:01: registered as thermal_zone1
[    2.759315] ACPI: Thermal Zone [TZ01] (30 C)
[    2.759343] GHES: HEST is not enabled!
[    2.759387] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.760268] Linux agpgart interface v0.103
[    2.760991] brd: module loaded
[    2.761385] loop: module loaded
[    2.761420] megasas: 06.600.18.00-rc1 Wed. May. 15 17:00:00 PDT 2013
[    2.761585] libphy: Fixed MDIO Bus: probed
[    2.761629] tun: Universal TUN/TAP device driver, 1.6
[    2.761629] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.761655] PPP generic driver version 2.4.2
[    2.761681] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.761682] ehci-pci: EHCI PCI platform driver
[    2.761753] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    2.761759] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    2.761762] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.761775] ehci-pci 0000:00:1a.0: debug port 2
[    2.765658] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    2.765669] ehci-pci 0000:00:1a.0: irq 16, io mem 0xef538000
[    2.774874] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.774887] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.774888] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.774889] usb usb1: Product: EHCI Host Controller
[    2.774890] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    2.774891] usb usb1: SerialNumber: 0000:00:1a.0
[    2.774957] hub 1-0:1.0: USB hub found
[    2.774961] hub 1-0:1.0: 2 ports detected
[    2.775086] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    2.775092] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.775094] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.775104] ehci-pci 0000:00:1d.0: debug port 2
[    2.778999] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.779010] ehci-pci 0000:00:1d.0: irq 23, io mem 0xef537000
[    2.790881] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.790889] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.790891] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.790892] usb usb2: Product: EHCI Host Controller
[    2.790893] usb usb2: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    2.790894] usb usb2: SerialNumber: 0000:00:1d.0
[    2.790948] hub 2-0:1.0: USB hub found
[    2.790950] hub 2-0:1.0: 2 ports detected
[    2.791009] ehci-platform: EHCI generic platform driver
[    2.791014] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.791015] ohci-pci: OHCI PCI platform driver
[    2.791020] ohci-platform: OHCI generic platform driver
[    2.791025] uhci_hcd: USB Universal Host Controller Interface driver
[    2.791094] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    2.791097] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.791099] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    2.791175] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    2.791189] xhci_hcd 0000:00:14.0: irq 45 for MSI/MSI-X
[    2.791226] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.791227] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.791228] usb usb3: Product: xHCI Host Controller
[    2.791229] usb usb3: Manufacturer: Linux 3.11.0-15-generic xhci_hcd
[    2.791230] usb usb3: SerialNumber: 0000:00:14.0
[    2.791271] xHCI xhci_add_endpoint called for root hub
[    2.791272] xHCI xhci_check_bandwidth called for root hub
[    2.791283] hub 3-0:1.0: USB hub found
[    2.791288] hub 3-0:1.0: 4 ports detected
[    2.791454] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.791457] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    2.791473] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    2.791475] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.791476] usb usb4: Product: xHCI Host Controller
[    2.791477] usb usb4: Manufacturer: Linux 3.11.0-15-generic xhci_hcd
[    2.791478] usb usb4: SerialNumber: 0000:00:14.0
[    2.791517] xHCI xhci_add_endpoint called for root hub
[    2.791518] xHCI xhci_check_bandwidth called for root hub
[    2.791530] hub 4-0:1.0: USB hub found
[    2.791535] hub 4-0:1.0: 4 ports detected
[    2.798914] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.799270] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.799273] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.799341] mousedev: PS/2 mouse device common for all mice
[    2.799425] rtc_cmos 00:05: RTC can wake from S4
[    2.799526] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.799550] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.799580] device-mapper: uevent: version 1.0.3
[    2.799616] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    2.799690] cpuidle: using governor ladder
[    2.799748] cpuidle: using governor menu
[    2.799755] ledtrig-cpu: registered to indicate activity on CPUs
[    2.799756] EFI Variables Facility v0.08 2004-May-17
[    2.805085] TCP: cubic registered
[    2.805139] NET: Registered protocol family 10
[    2.805244] NET: Registered protocol family 17
[    2.805249] Key type dns_resolver registered
[    2.805398] PM: Hibernation image not present or could not be loaded.
[    2.805400] Loading module verification certificates
[    2.805965] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: e20ade5b3af83aaa8563f0ef4119a030c4d3ffdb'
[    2.805972] registered taskstats version 1
[    2.807443] Key type trusted registered
[    2.808955] Key type encrypted registered
[    2.810321] AppArmor: AppArmor sha1 policy hashing enabled
[    2.810753]   Magic number: 2:704:674
[    2.810865] rtc_cmos 00:05: setting system clock to 2014-02-10 08:39:28 UTC (1392021568)
[    2.811354] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.811355] EDD information not available.
[    2.812237] Freeing unused kernel memory: 1392K (ffffffff81d0f000 - ffffffff81e6b000)
[    2.812238] Write protecting the kernel read-only data: 12288k
[    2.813333] Freeing unused kernel memory: 672K (ffff880001758000 - ffff880001800000)
[    2.813436] Freeing unused kernel memory: 20K (ffff880001bfb000 - ffff880001c00000)
[    2.824436] udevd[122]: starting version 175
[    2.844683] pps_core: LinuxPPS API ver. 1 registered
[    2.844686] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    2.844954] wmi: Mapper loaded
[    2.845447] PTP clock support registered
[    2.848029] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    2.848031] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    2.848124] e1000e 0000:00:19.0: setting latency timer to 64
[    2.848171] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.848185] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[    2.851688] [drm] Initialized drm 1.1.0 20060810
[    2.862746] MXM: GUID detected in BIOS
[    2.862761] checking generic (d9000000 1e0000) vs hw (d0000000 8000000)
[    2.862762] checking generic (d9000000 1e0000) vs hw (d8000000 2000000)
[    2.862763] fb: conflicting fb hw usage nouveaufb vs EFI VGA - removing generic driver
[    2.862774] Console: switching to colour dummy device 80x25
[    2.863408] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x0e4030a2
[    2.863411] nouveau  [  DEVICE][0000:01:00.0] Chipset: GK104 (NVE4)
[    2.863412] nouveau  [  DEVICE][0000:01:00.0] Family : NVE0
[    2.865018] firewire_ohci 0000:69:01.0: enabling device (0000 -> 0003)
[    2.865153] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[    2.865159] nouveau  [   VBIOS][0000:01:00.0] ... signature not found
[    2.865160] nouveau  [   VBIOS][0000:01:00.0] checking PROM for image...
[    2.935003] firewire_ohci 0000:69:01.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    2.967884] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[    2.967886] nouveau  [   VBIOS][0000:01:00.0] using image from PROM
[    2.967963] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[    2.967965] nouveau  [   VBIOS][0000:01:00.0] version 80.04.4b.00.16
[    2.971170] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR5
[    2.971172] nouveau  [     PFB][0000:01:00.0] RAM size: 2048 MiB
[    2.971173] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
[    2.994614] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[    2.994618] nouveau  [  PTHERM][0000:01:00.0] fan management: disabled
[    2.994620] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[    3.019810] [TTM] Zone  kernel: Available graphics memory: 8193420 kiB
[    3.019812] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    3.019813] [TTM] Initializing pool allocator
[    3.019815] [TTM] Initializing DMA pool allocator
[    3.019822] nouveau  [     DRM] VRAM: 2048 MiB
[    3.019823] nouveau  [     DRM] GART: 1048576 MiB
[    3.019825] nouveau  [     DRM] TMDS table version 2.0
[    3.019826] nouveau  [     DRM] DCB version 4.0
[    3.019828] nouveau  [     DRM] DCB outp 00: 01000f02 00020030
[    3.019829] nouveau  [     DRM] DCB outp 01: 02000f00 00000000
[    3.019830] nouveau  [     DRM] DCB outp 02: 08011f82 00020030
[    3.019831] nouveau  [     DRM] DCB outp 03: 02822f62 0f420010
[    3.019832] nouveau  [     DRM] DCB outp 05: 04833fb6 0f420010
[    3.019833] nouveau  [     DRM] DCB outp 06: 04033f72 00020010
[    3.019835] nouveau  [     DRM] DCB conn 00: 00001030
[    3.019836] nouveau  [     DRM] DCB conn 01: 00020131
[    3.019837] nouveau  [     DRM] DCB conn 02: 00002261
[    3.019838] nouveau  [     DRM] DCB conn 03: 00010346
[    3.019839] nouveau  [     DRM] DCB conn 04: 00000460
[    3.020690] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.020691] [drm] No driver support for vblank timestamp query.
[    3.020776] nouveau W[     DRM] voltage table 0x50 unknown
[    3.020780] nouveau  [     DRM] 4 available performance level(s)
[    3.020782] nouveau  [     DRM] 0: core 162MHz shader 324MHz memory 648MHz voltage 100mV
[    3.020784] nouveau  [     DRM] 1: core 405MHz shader 810MHz memory 1080MHz voltage 80mV
[    3.020785] nouveau  [     DRM] 2: core 1502MHz shader 3004MHz memory 1080MHz voltage 60mV
[    3.020787] nouveau  [     DRM] 3: core 1502MHz shader 3004MHz memory 1080MHz voltage 40mV
[    3.020788] nouveau  [     DRM] c:
[    3.030451] nouveau  [     DRM] MM: using COPY for buffer copies
[    3.123284] e1000e 0000:00:19.0 eth0: registered PHC clock
[    3.123287] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 88:88:88:88:87:88
[    3.123288] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    3.123376] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    3.123419] ahci 0000:00:1f.2: version 3.0
[    3.123531] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
[    3.123616] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
[    3.123618] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    3.123622] ahci 0000:00:1f.2: setting latency timer to 64
[    3.131363] scsi0 : ahci
[    3.131490] scsi1 : ahci
[    3.131591] scsi2 : ahci
[    3.131672] scsi3 : ahci
[    3.131757] scsi4 : ahci
[    3.131825] scsi5 : ahci
[    3.131881] ata1: SATA max UDMA/133 abar m2048@0xef536000 port 0xef536100 irq 47
[    3.131884] ata2: SATA max UDMA/133 abar m2048@0xef536000 port 0xef536180 irq 47
[    3.131885] ata3: DUMMY
[    3.131885] ata4: DUMMY
[    3.131886] ata5: DUMMY
[    3.131887] ata6: DUMMY
[    3.131971] ahci 0000:6a:00.0: irq 48 for MSI/MSI-X
[    3.132091] ahci 0000:6a:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    3.132093] ahci 0000:6a:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
[    3.132333] scsi6 : ahci
[    3.132414] scsi7 : ahci
[    3.132450] ata7: SATA max UDMA/133 abar m512@0xef310000 port 0xef310100 irq 48
[    3.132454] ata8: SATA max UDMA/133 abar m512@0xef310000 port 0xef310180 irq 48
[    3.179055] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    3.198674] nouveau  [     DRM] allocated 1920x1080 fb: 0x80000, bo ffff8804166d6800
[    3.198759] fbcon: nouveaufb (fb0) is primary device
[    3.259947] Console: switching to colour frame buffer device 240x67
[    3.261240] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[    3.261241] nouveau 0000:01:00.0: registered panic notifier
[    3.261243] [drm] Initialized nouveau 1.1.1 20120801 for 0000:01:00.0 on minor 0
[    3.311477] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    3.311482] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.311722] hub 1-1:1.0: USB hub found
[    3.311799] hub 1-1:1.0: 6 ports detected
[    3.423159] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    3.435315] firewire_core 0000:69:01.0: created device fw0: GUID ffed2000ffffffff, S400
[    3.451208] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    3.451219] ata7: SATA link down (SStatus 0 SControl 300)
[    3.451259] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    3.451269] ata8: SATA link down (SStatus 0 SControl 300)
[    3.451828] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[    3.451833] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8804184defc8), AE_NOT_FOUND (20130517/psparse-536)
[    3.451873] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[    3.451877] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8804184f4050), AE_NOT_FOUND (20130517/psparse-536)
[    3.451906] ata2.00: ATA-9: OCZ-VERTEX4, 1.5, max UDMA/133
[    3.451908] ata2.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.452051] ata1.00: ATA-8: ST1500DL003-9VT16L, CC4A, max UDMA/133
[    3.452056] ata1.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.452543] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[    3.452547] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8804184f4050), AE_NOT_FOUND (20130517/psparse-536)
[    3.452583] ata2.00: configured for UDMA/133
[    3.452682] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
[    3.452686] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8804184defc8), AE_NOT_FOUND (20130517/psparse-536)
[    3.452922] ata1.00: configured for UDMA/133
[    3.453120] scsi 0:0:0:0: Direct-Access     ATA      ST1500DL003-9VT1 CC4A PQ: 0 ANSI: 5
[    3.453214] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.453240] sd 0:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    3.453242] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    3.453276] sd 0:0:0:0: [sda] Write Protect is off
[    3.453278] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.453289] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.453339] scsi 1:0:0:0: Direct-Access     ATA      OCZ-VERTEX4      1.5  PQ: 0 ANSI: 5
[    3.453430] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    3.453479] sd 1:0:0:0: [sdb] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    3.453519] sd 1:0:0:0: [sdb] Write Protect is off
[    3.453521] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.453533] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.454687]  sdb: sdb1 sdb2
[    3.455236] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.525773]  sda: sda1 sda2
[    3.526294] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.559563] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    3.559567] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.559818] hub 2-1:1.0: USB hub found
[    3.559914] hub 2-1:1.0: 8 ports detected
[    3.719256] tsc: Refined TSC clocksource calibration: 3403.347 MHz
[    3.727266] usb 3-4: new full-speed USB device number 2 using xhci_hcd
[    3.745671] usb 3-4: New USB device found, idVendor=0a5c, idProduct=21e8
[    3.745673] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.745674] usb 3-4: Product: BCM20702A0
[    3.745675] usb 3-4: Manufacturer: Broadcom Corp
[    3.745676] usb 3-4: SerialNumber: 0002723F46E3
[    3.857432] usb 4-3: new SuperSpeed USB device number 2 using xhci_hcd
[    3.925988] usb 4-3: New USB device found, idVendor=2109, idProduct=0810
[    3.925991] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.925993] usb 4-3: Product: 4-Port USB 3.0 Hub
[    3.925994] usb 4-3: Manufacturer: VIA Labs, Inc.
[    3.943109] xor: automatically using best checksumming function:
[    3.949150] hub 4-3:1.0: USB hub found
[    3.952495] hub 4-3:1.0: 4 ports detected
[    3.979346]    avx       : 25661.000 MB/sec
[    4.047379] raid6: sse2x1    9218 MB/s
[    4.097832] usb 4-4: new SuperSpeed USB device number 3 using xhci_hcd
[    4.115406] raid6: sse2x2   11564 MB/s
[    4.166621] usb 4-4: New USB device found, idVendor=2109, idProduct=0810
[    4.166623] usb 4-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.166624] usb 4-4: Product: 4-Port USB 3.0 Hub
[    4.166625] usb 4-4: Manufacturer: VIA Labs, Inc.
[    4.183428] raid6: sse2x4   13431 MB/s
[    4.183429] raid6: using algorithm sse2x4 (13431 MB/s)
[    4.183430] raid6: using ssse3x2 recovery algorithm
[    4.187436] hub 4-4:1.0: USB hub found
[    4.190767] hub 4-4:1.0: 4 ports detected
[    4.191209] bio: create slab <bio-1> at 1
[    4.191359] Btrfs loaded
[    4.197372] device-mapper: dm-raid45: initialized v0.2594b
[    4.295561] usb 1-1.1: new high-speed USB device number 3 using ehci-pci
[    4.396523] usb 1-1.1: New USB device found, idVendor=05ac, idProduct=1006
[    4.396528] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.396531] usb 1-1.1: Product: Keyboard Hub
[    4.396533] usb 1-1.1: Manufacturer: Apple, Inc.
[    4.396535] usb 1-1.1: SerialNumber: 000000000000
[    4.396767] hub 1-1.1:1.0: USB hub found
[    4.396870] hub 1-1.1:1.0: 3 ports detected
[    4.467657] usb 1-1.5: new high-speed USB device number 4 using ehci-pci
[    4.560965] usb 1-1.5: New USB device found, idVendor=2109, idProduct=0810
[    4.560970] usb 1-1.5: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    4.560972] usb 1-1.5: Product: USB2.0 Hub
[    4.561365] hub 1-1.5:1.0: USB hub found
[    4.561596] hub 1-1.5:1.0: 4 ports detected
[    4.639728] usb 2-1.6: new high-speed USB device number 3 using ehci-pci
[    4.719866] Switched to clocksource tsc
[    4.734670] usb 2-1.6: New USB device found, idVendor=0781, idProduct=540c
[    4.734675] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    4.734678] usb 2-1.6: Product: U3 Flash Drive
[    4.734680] usb 2-1.6: Manufacturer:                         
[    4.734682] usb 2-1.6: SerialNumber: 0000167A677277B1
[    4.737485] usb-storage 2-1.6:1.0: USB Mass Storage device detected
[    4.737653] scsi8 : usb-storage 2-1.6:1.0
[    4.737699] usbcore: registered new interface driver usb-storage
[    4.803772] usb 1-1.1.1: new low-speed USB device number 5 using ehci-pci
[    4.901331] usb 1-1.1.1: New USB device found, idVendor=05ac, idProduct=0304
[    4.901336] usb 1-1.1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.901339] usb 1-1.1.1: Product: Apple Optical USB Mouse
[    4.901341] usb 1-1.1.1: Manufacturer: Mitsumi Electric
[    4.904379] hidraw: raw HID events driver (C) Jiri Kosina
[    4.907443] usbcore: registered new interface driver usbhid
[    4.907445] usbhid: USB HID core driver
[    4.909297] input: Mitsumi Electric Apple Optical USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.1/1-1.1.1:1.0/input/input2
[    4.909498] apple 0003:05AC:0304.0001: input,hidraw0: USB HID v1.10 Mouse [Mitsumi Electric Apple Optical USB Mouse] on usb-0000:00:1a.0-1.1.1/input0
[    4.971850] usb 1-1.1.2: new low-speed USB device number 6 using ehci-pci
[    5.070877] usb 1-1.1.2: New USB device found, idVendor=05ac, idProduct=0221
[    5.070879] usb 1-1.1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    5.070880] usb 1-1.1.2: Product: Apple Keyboard
[    5.070881] usb 1-1.1.2: Manufacturer: Apple, Inc
[    5.074613] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.2/1-1.1.2:1.0/input/input3
[    5.074780] apple 0003:05AC:0221.0002: input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:1a.0-1.1.2/input0
[    5.077860] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.2/1-1.1.2:1.1/input/input4
[    5.078020] apple 0003:05AC:0221.0003: input,hidraw2: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:1a.0-1.1.2/input1
[    5.736897] scsi 8:0:0:0: Direct-Access              U3 Flash Drive   2.20 PQ: 0 ANSI: 2
[    5.737333] scsi 8:0:0:1: CD-ROM                     U3 Flash Drive   2.20 PQ: 0 ANSI: 2
[    5.737553] sd 8:0:0:0: Attached scsi generic sg2 type 0
[    5.740023] sd 8:0:0:0: [sdc] 4001425 512-byte logical blocks: (2.04 GB/1.90 GiB)
[    5.740651] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[    5.740653] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.740749] sr 8:0:0:1: Attached scsi CD-ROM sr0
[    5.740848] sr 8:0:0:1: Attached scsi generic sg3 type 5
[    5.741249] sd 8:0:0:0: [sdc] Write Protect is off
[    5.741252] sd 8:0:0:0: [sdc] Mode Sense: 03 00 00 00
[    5.742245] sd 8:0:0:0: [sdc] No Caching mode page found
[    5.742247] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[    5.748318] sd 8:0:0:0: [sdc] No Caching mode page found
[    5.748321] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[    5.778093]  sdc: sdc1
[    5.789338] sd 8:0:0:0: [sdc] No Caching mode page found
[    5.789340] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[    5.789342] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[    8.026413] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   14.796336] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.830130] udevd[1524]: starting version 175
[   15.193108] lp: driver loaded but no devices found
[   15.252344] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[   15.252349] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.252352] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   15.252354] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.252355] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \LED_ 1 (20130517/utaddress-251)
[   15.252357] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 2 (20130517/utaddress-251)
[   15.252358] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.252359] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   15.264685] ppdev: user-space parallel port driver
[   15.269700] Bluetooth: Core ver 2.16
[   15.269712] NET: Registered protocol family 31
[   15.269714] Bluetooth: HCI device and connection manager initialized
[   15.269719] Bluetooth: HCI socket layer initialized
[   15.269721] Bluetooth: L2CAP socket layer initialized
[   15.269724] Bluetooth: SCO socket layer initialized
[   15.360202] Bluetooth: RFCOMM TTY layer initialized
[   15.360212] Bluetooth: RFCOMM socket layer initialized
[   15.360213] Bluetooth: RFCOMM ver 1.11
[   15.370154] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.370157] Bluetooth: BNEP filters: protocol multicast
[   15.370162] Bluetooth: BNEP socket layer initialized
[   15.385823] device-mapper: multipath: version 1.5.1 loaded
[   15.474598] usbcore: registered new interface driver btusb
[   15.575174] Bluetooth: can't load firmware, may not work correctly
[   15.700258] init: failsafe main process (1847) killed by TERM signal
[   15.724167] mei_me 0000:00:16.0: setting latency timer to 64
[   15.724202] mei_me 0000:00:16.0: irq 49 for MSI/MSI-X
[   15.818198] cfg80211: Calling CRDA to update world regulatory domain
[   16.002942] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   16.003051] snd_hda_intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[   16.080315] SKU: Nid=0x1d sku_cfg=0x4007e619
[   16.080317] SKU: port_connectivity=0x1
[   16.080318] SKU: enable_pcbeep=0x0
[   16.080319] SKU: check_sum=0x00000007
[   16.080320] SKU: customization=0x000000e6
[   16.080320] SKU: external_amp=0x3
[   16.080321] SKU: platform_type=0x0
[   16.080321] SKU: swap=0x0
[   16.080322] SKU: override=0x1
[   16.080760] autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[   16.080761]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.080762]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   16.080763]    mono: mono_out=0x0
[   16.080763]    dig-out=0x11/0x1e
[   16.080764]    inputs:
[   16.080765]      Front Mic=0x19
[   16.080766]      Rear Mic=0x18
[   16.080767]      Line=0x1a
[   16.080767]    dig-in=0x1f
[   16.080768] realtek: No valid SSID, checking pincfg 0x4007e619 for NID 0x1d
[   16.080769] realtek: Enabling init ASM_ID=0xe619 CODEC_ID=10ec0899
[   16.092067] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   16.092136] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   16.092181] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.092214] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.092248] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.092280] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.092313] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.092465] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[   16.092508] hda_intel: Disabling MSI
[   16.092513] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.092544] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   16.095793] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   16.263939] ath9k 0000:67:00.0: enabling device (0000 -> 0002)
[   16.346160] ath: EEPROM regdomain: 0x21
[   16.346162] ath: EEPROM indicates we should expect a direct regpair map
[   16.346163] ath: Country alpha2 being used: AU
[   16.346164] ath: Regpair used: 0x21
[   16.444867] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   16.445208] ieee80211 phy0: Atheros AR9300 Rev:3 mem=0xffffc90012d80000, irq=19
[   16.617101] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   16.619520] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   16.619584] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   16.619639] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[   16.952996] init: alsa-restore main process (2052) terminated with status 99
[   17.002733] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   17.104627] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   17.104713] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.104918] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.112074] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.112218] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   62.394675] usb 2-1.5: new high-speed USB device number 4 using ehci-pci
[   62.492105] usb 2-1.5: New USB device found, idVendor=0951, idProduct=1689
[   62.492110] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   62.492113] usb 2-1.5: Product: DataTraveler SE9
[   62.492115] usb 2-1.5: Manufacturer: Kingston
[   62.492117] usb 2-1.5: SerialNumber: 50E549513589BBA040000241
[   62.492369] usb-storage 2-1.5:1.0: USB Mass Storage device detected
[   62.492519] scsi9 : usb-storage 2-1.5:1.0
[   63.564153] scsi 9:0:0:0: Direct-Access     Kingston DataTraveler SE9 PMAP PQ: 0 ANSI: 4
[   63.564386] sd 9:0:0:0: Attached scsi generic sg4 type 0
[   65.409784] sd 9:0:0:0: [sdd] 15470592 512-byte logical blocks: (7.92 GB/7.37 GiB)
[   65.411220] sd 9:0:0:0: [sdd] Write Protect is off
[   65.411224] sd 9:0:0:0: [sdd] Mode Sense: 23 00 00 00
[   65.412619] sd 9:0:0:0: [sdd] No Caching mode page found
[   65.412622] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[   65.417678] sd 9:0:0:0: [sdd] No Caching mode page found
[   65.417680] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[   65.441172]  sdd: sdd1
[   65.445865] sd 9:0:0:0: [sdd] No Caching mode page found
[   65.445870] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[   65.445874] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[   65.768526] hfsplus: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[  147.664634] usb 1-1.1.3: new high-speed USB device number 7 using ehci-pci
[  148.631042] usb 1-1.1.3: New USB device found, idVendor=058f, idProduct=1234
[  148.631047] usb 1-1.1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  148.631050] usb 1-1.1.3: Product: Mass Storage Device
[  148.631052] usb 1-1.1.3: Manufacturer: Alcor Micro
[  148.631438] usb-storage 1-1.1.3:1.0: USB Mass Storage device detected
[  148.631609] scsi10 : usb-storage 1-1.1.3:1.0
[  149.630293] scsi 10:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
[  149.630617] sd 10:0:0:0: Attached scsi generic sg5 type 0
[  149.632754] sd 10:0:0:0: [sde] Attached SCSI removable disk
[  149.874964] sdd: detected capacity change from 7920943104 to 0
[  158.489861] usb 2-1.5: USB disconnect, device number 4
[  162.574581] usb 1-1.1.3: USB disconnect, device number 7
[  167.684494] usb 3-2: new high-speed USB device number 3 using xhci_hcd
[  168.134748] usb 3-2: New USB device found, idVendor=058f, idProduct=1234
[  168.134753] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  168.134755] usb 3-2: Product: Mass Storage Device
[  168.134758] usb 3-2: Manufacturer: Alcor Micro
[  168.135159] usb-storage 3-2:1.0: USB Mass Storage device detected
[  168.135295] scsi11 : usb-storage 3-2:1.0
[  169.133661] scsi 11:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
[  169.133957] sd 11:0:0:0: Attached scsi generic sg4 type 0
[  169.134903] sd 11:0:0:0: [sdd] Attached SCSI removable disk
[  190.901419] usb 3-2: USB disconnect, device number 3
[  199.409233] usb 2-1.5: new high-speed USB device number 5 using ehci-pci
[  199.501981] usb 2-1.5: New USB device found, idVendor=abcd, idProduct=1234
[  199.501986] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  199.501989] usb 2-1.5: Product: DISK            
[  199.501991] usb 2-1.5: Manufacturer: USB     
[  199.501993] usb 2-1.5: SerialNumber: 1309041408432274706204
[  199.502266] usb-storage 2-1.5:1.0: USB Mass Storage device detected
[  199.502411] scsi12 : usb-storage 2-1.5:1.0
[  200.502174] scsi 12:0:0:0: Direct-Access     USB      DISK             5.00 PQ: 0 ANSI: 2
[  200.502454] sd 12:0:0:0: Attached scsi generic sg4 type 0
[  200.503121] sd 12:0:0:0: [sdd] 7884800 512-byte logical blocks: (4.03 GB/3.75 GiB)
[  200.504013] sd 12:0:0:0: [sdd] Write Protect is off
[  200.504018] sd 12:0:0:0: [sdd] Mode Sense: 0b 00 00 08
[  200.505163] sd 12:0:0:0: [sdd] No Caching mode page found
[  200.505167] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[  200.507628] sd 12:0:0:0: [sdd] No Caching mode page found
[  200.507632] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[  200.508151]  sdd:
[  200.510757] sd 12:0:0:0: [sdd] No Caching mode page found
[  200.510763] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[  200.510766] sd 12:0:0:0: [sdd] Attached SCSI removable disk
[  200.659817] FAT-fs (sdd): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

```

---

### Post by tgalati4 on 2014-02-10
Open a terminal and post the output of:

```
aplay -l
```

Get friendly with 

```
speaker-test
```

Some things to try:  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by Yellow Pasque on 2014-02-10
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by juliushibert63 on 2014-02-11
> **tgalati4 said:**
> Open a terminal and post the output of:

```
aplay -l
```

Get friendly with 

```
speaker-test
```

Some things to try:  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)


Here's the output from 
```
aplay -l
```

```
**** List of PLAYBACK Hardware Devices ****card 0: PCH [HDA Intel PCH], device 0: ALC898 Analog [ALC898 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC898 Digital [ALC898 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I also tried using speaker-test with various options but still couldn't get any sound out of my speakers or sound card.



> [COLOR=#000000]Temüjin[/COLOR][COLOR=#000000][INDENT]**Re: Think my mobo sound is dead... Trying to trouble shoot it**
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)[/INDENT][/COLOR]


Here's is the output from Alsa-info

```
upload=true&script=true&cardinfo=!!################################
!!ALSA Information Script v 0.4.62
!!################################


!!Script ran on: Tue Feb 11 08:17:09 UTC 2014




!!Linux Distribution
!!------------------


Ubuntu 12.04.4 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.4 LTS)"




!!DMI Information
!!---------------


Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      To be filled by O.E.M.
Product Version:   To be filled by O.E.M.
Firmware Version:  F11




!!Kernel Information
!!------------------


Kernel release:    3.11.0-15-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k3.11.0-15-generic
Library version:    1.0.25
Utilities version:  1.0.25




!!Loaded ALSA modules
!!-------------------


snd_hda_intel
snd_hda_intel




!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------


 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xef530000 irq 50
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xe7080000 irq 17




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)




!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------


00:1b.0 0403: 8086:1e20 (rev 04)
	Subsystem: 1458:a072
--
01:00.1 0403: 10de:0e0a (rev a1)
	Subsystem: 1462:2843




!!Modprobe options (Sound related)
!!--------------------------------


snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2




!!Loaded sound module options
!!---------------------------


!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : Y


!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : Y




!!HDA-Intel Codec information
!!---------------------------
--startcollapse--


Codec: Realtek ALC898
Address: 2
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0899
Subsystem Id: 0x1458a072
Revision Id: 0x100003
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
Node 0x02 [Audio Output] wcaps 0x411: Stereo
  Device: name="ALC898 Analog", type="Audio", device=0
  Converter: stream=8, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=8, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC898 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x27 0x27]
  Converter: stream=4, channel=0
  SDI-Select: 0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC898 Alt Analog", type="Audio", device=2
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=2, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=2, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x3f, stepsize=0x02, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100791: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="ALC898 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x570]: 32000 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Rear Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x3d 0x3d]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x3d 0x3d]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x3d 0x3d]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x3d 0x3d]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC898 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400701: Stereo Digital
  Control: name="SPDIF Phantom Jack", index=0, device=0
  Pincap 0x00000010: OUT
  Pin Default 0x99430130: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line Out Front Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x01014410: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Line Out Surround Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x01011412: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=06, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Control: name="Line Out CLFE Jack", index=0, device=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x01016411: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=07, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Rear Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19c50: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c60: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Line Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181345f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Headphone Jack", index=0, device=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214020: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4007e619: [N/A] Line Out at Ext N/A
    Conn = Analog, Color = White
    DefAssociation = 0x1, Sequence = 0x9
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400701: Stereo Digital
  Control: name="SPDIF Phantom Jack", index=1, device=0
  Pincap 0x00000010: OUT
  Pin Default 0x01452140: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Grey
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Control: name="SPDIF In Phantom Jack", index=0, device=0
  Pincap 0x00000020: IN
  Pin Default 0x99c30170: [Fixed] SPDIF In at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x7, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=28
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 12
     0x18 0x19* 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x25 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x57, nsteps=0x57, stepsize=0x02, mute=0
  Amp-Out vals:  [0x57 0x57]
  Connection: 2
     0x25 0x0b
Codec: Nvidia GPU 40 HDMI/DP
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0040
Subsystem Id: 0x14622843
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=01, enabled=1
  Connection: 4
     0x08* 0x09 0x0a 0x0b
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=7 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Control: name="ELD", index=0, device=7
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=02, enabled=1
  Connection: 4
     0x08* 0x09 0x0a 0x0b
Node 0x06 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=8 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Control: name="ELD", index=0, device=8
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=03, enabled=1
  Connection: 4
     0x08* 0x09 0x0a 0x0b
Node 0x07 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="HDMI/DP,pcm=9 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Control: name="ELD", index=0, device=9
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x185600f0: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=04, enabled=1
  Connection: 4
     0x08* 0x09 0x0a 0x0b
Node 0x08 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=8, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x09 [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x0a [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x0b [Audio Output] wcaps 0x62b1: 8-Channels Digital Stripe
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
--endcollapse--




!!ALSA Device nodes
!!-----------------


crw-rw---T+ 1 root audio 116,  8 Feb 11 08:06 /dev/snd/controlC0
crw-rw---T+ 1 root audio 116, 14 Feb 11 08:06 /dev/snd/controlC1
crw-rw---T+ 1 root audio 116,  7 Feb 11 08:06 /dev/snd/hwC0D2
crw-rw---T+ 1 root audio 116, 13 Feb 11 08:06 /dev/snd/hwC1D0
crw-rw---T+ 1 root audio 116,  6 Feb 11 08:06 /dev/snd/pcmC0D0c
crw-rw---T+ 1 root audio 116,  5 Feb 11 08:16 /dev/snd/pcmC0D0p
crw-rw---T+ 1 root audio 116,  4 Feb 11 08:06 /dev/snd/pcmC0D1c
crw-rw---T+ 1 root audio 116,  3 Feb 11 08:06 /dev/snd/pcmC0D1p
crw-rw---T+ 1 root audio 116,  2 Feb 11 08:06 /dev/snd/pcmC0D2c
crw-rw---T+ 1 root audio 116, 12 Feb 11 08:06 /dev/snd/pcmC1D3p
crw-rw---T+ 1 root audio 116, 11 Feb 11 08:06 /dev/snd/pcmC1D7p
crw-rw---T+ 1 root audio 116, 10 Feb 11 08:06 /dev/snd/pcmC1D8p
crw-rw---T+ 1 root audio 116,  9 Feb 11 08:06 /dev/snd/pcmC1D9p
crw-rw---T+ 1 root audio 116,  1 Feb 11 08:06 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Feb 11 08:06 /dev/snd/timer


/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Feb 11 08:06 .
drwxr-xr-x 3 root root 360 Feb 11 08:06 ..
lrwxrwxrwx 1 root root  12 Feb 11 08:06 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 Feb 11 08:06 pci-0000:01:00.1 -> ../controlC1




!!Aplay/Arecord output
!!--------------------


APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC898 Analog [ALC898 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC898 Digital [ALC898 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ARECORD


**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC898 Analog [ALC898 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC898 Digital [ALC898 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: ALC898 Alt Analog [ALC898 Alt Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1


!!Amixer output
!!-------------


!!-------Mixer controls for card 0 [PCH]


Card hw:0 'PCH'/'HDA Intel PCH at 0xef530000 irq 50'
  Mixer name	: 'Realtek ALC898'
  Components	: 'HDA:10ec0899,1458a072,00100003'
  Controls      : 55
  Simple ctrls  : 22
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 61 [70%] [-19.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 87 [100%] [0.00dB] [on]
  Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Line Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 39 [62%] [12.00dB] [on]
  Front Right: Capture 39 [62%] [12.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 0 [0%] [-17.25dB] [off]
  Front Right: Capture 0 [0%] [-17.25dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 63
  Front Left: Capture 0 [0%] [-17.25dB] [off]
  Front Right: Capture 0 [0%] [-17.25dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]


!!-------Mixer controls for card 1 [NVidia]


Card hw:1 'NVidia'/'HDA NVidia at 0xe7080000 irq 17'
  Mixer name	: 'Nvidia GPU 40 HDMI/DP'
  Components	: 'HDA:10de0040,14622843,00100100'
  Controls      : 28
  Simple ctrls  : 4
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',3
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]




!!Alsactl output
!!--------------


--startcollapse--
state.PCH {
	control.1 {
		iface MIXER
		name 'Front Playback Volume'
		value.0 87
		value.1 87
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.2 {
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Surround Playback Volume'
		value.0 87
		value.1 87
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Center Playback Volume'
		value 87
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 0
		}
	}
	control.6 {
		iface MIXER
		name 'LFE Playback Volume'
		value 87
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 0
		}
	}
	control.7 {
		iface MIXER
		name 'Center Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'LFE Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.9 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 87
		value.1 87
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.10 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.11 {
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.12 {
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.13 {
		iface MIXER
		name 'Rear Mic Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.14 {
		iface MIXER
		name 'Rear Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.15 {
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.16 {
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.17 {
		iface MIXER
		name 'Auto-Mute Mode'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.18 {
		iface MIXER
		name 'Input Source'
		value 'Front Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Front Mic'
			item.1 'Rear Mic'
			item.2 Line
		}
	}
	control.19 {
		iface MIXER
		name 'Input Source'
		index 1
		value 'Front Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Front Mic'
			item.1 'Rear Mic'
			item.2 Line
		}
	}
	control.20 {
		iface MIXER
		name 'Input Source'
		index 2
		value 'Front Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Front Mic'
			item.1 'Rear Mic'
			item.2 Line
		}
	}
	control.21 {
		iface MIXER
		name 'Capture Volume'
		value.0 39
		value.1 39
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 63'
			dbmin -1725
			dbmax 3000
			dbvalue.0 1200
			dbvalue.1 1200
		}
	}
	control.22 {
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.23 {
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 63'
			dbmin -1725
			dbmax 3000
			dbvalue.0 -1725
			dbvalue.1 -1725
		}
	}
	control.24 {
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.25 {
		iface MIXER
		name 'Capture Volume'
		index 2
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 63'
			dbmin -1725
			dbmax 3000
			dbvalue.0 -1725
			dbvalue.1 -1725
		}
	}
	control.26 {
		iface MIXER
		name 'Capture Switch'
		index 2
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.27 {
		iface MIXER
		name 'Front Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.28 {
		iface MIXER
		name 'Rear Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.29 {
		iface MIXER
		name 'Line Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.30 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.31 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.32 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.33 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.34 {
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.35 {
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.36 {
		iface MIXER
		name 'IEC958 Capture Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.37 {
		iface MIXER
		name 'Master Playback Volume'
		value 61
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 87'
			dbmin -6525
			dbmax 0
			dbvalue.0 -1950
		}
	}
	control.38 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.39 {
		iface CARD
		name 'Front Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.40 {
		iface CARD
		name 'Rear Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.41 {
		iface CARD
		name 'Line Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.42 {
		iface CARD
		name 'Line Out Front Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.43 {
		iface CARD
		name 'Line Out Surround Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.44 {
		iface CARD
		name 'Line Out CLFE Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.45 {
		iface CARD
		name 'Front Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.46 {
		iface CARD
		name 'SPDIF Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.47 {
		iface CARD
		name 'SPDIF Phantom Jack'
		index 1
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.48 {
		iface CARD
		name 'SPDIF In Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.49 {
		iface PCM
		name 'Playback Channel Map'
		value.0 3
		value.1 4
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		comment {
			access read
			type INTEGER
			count 6
			range '0 - 36'
		}
	}
	control.50 {
		iface PCM
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.51 {
		iface PCM
		device 1
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.52 {
		iface PCM
		device 1
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.53 {
		iface PCM
		device 2
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.54 {
		iface PCM
		device 2
		name 'Capture Channel Map'
		index 1
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.55 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
state.NVidia {
	control.1 {
		iface CARD
		name 'HDMI/DP,pcm=3 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.5 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface PCM
		device 3
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.7 {
		iface CARD
		name 'HDMI/DP,pcm=7 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 1
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.9 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 1
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.10 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 1
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.11 {
		iface MIXER
		name 'IEC958 Playback Switch'
		index 1
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface PCM
		device 7
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.13 {
		iface CARD
		name 'HDMI/DP,pcm=8 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 2
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.15 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 2
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.16 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 2
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.17 {
		iface MIXER
		name 'IEC958 Playback Switch'
		index 2
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.18 {
		iface PCM
		device 8
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.19 {
		iface CARD
		name 'HDMI/DP,pcm=9 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.20 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 3
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.21 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 3
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.22 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 3
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.23 {
		iface MIXER
		name 'IEC958 Playback Switch'
		index 3
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.24 {
		iface PCM
		device 9
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.25 {
		iface PCM
		device 3
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
	control.26 {
		iface PCM
		device 7
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
	control.27 {
		iface PCM
		device 8
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
	control.28 {
		iface PCM
		device 9
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
}
--endcollapse--




!!All Loaded Modules
!!------------------


Module
dm_crypt
snd_hda_codec_hdmi
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
arc4
snd_hwdep
ath9k
snd_pcm
mac80211
snd_seq_midi
ath9k_common
ath9k_hw
snd_rawmidi
ath
snd_seq_midi_event
cfg80211
snd_seq
snd_timer
snd_seq_device
rfcomm
bnep
btusb
bluetooth
psmouse
snd
parport_pc
soundcore
mei_me
dm_multipath
snd_page_alloc
mei
serio_raw
mac_hid
ppdev
lpc_ich
scsi_dh
lp
parport
squashfs
overlayfs
hid_apple
usbhid
hid
usb_storage
nls_iso8859_1
dm_raid45
dm_mirror
dm_region_hash
dm_log
btrfs
raid6_pq
xor
zlib_deflate
nouveau
firewire_ohci
firewire_core
crc_itu_t
ttm
drm_kms_helper
ahci
libahci
e1000e
drm
i2c_algo_bit
mxm_wmi
video
wmi
ptp
pps_core




!!Sysfs Files
!!-----------


/sys/class/sound/hwC0D2/init_pin_configs:
0x11 0x99430130
0x12 0x411111f0
0x14 0x01014410
0x15 0x01011412
0x16 0x01016411
0x17 0x411111f0
0x18 0x01a19c50
0x19 0x02a19c60
0x1a 0x0181345f
0x1b 0x02214020
0x1c 0x411111f0
0x1d 0x4007e619
0x1e 0x01452140
0x1f 0x99c30170


/sys/class/sound/hwC0D2/driver_pin_configs:


/sys/class/sound/hwC0D2/user_pin_configs:


/sys/class/sound/hwC0D2/init_verbs:


/sys/class/sound/hwC0D2/hints:


/sys/class/sound/hwC1D0/init_pin_configs:
0x04 0x185600f0
0x05 0x185600f0
0x06 0x185600f0
0x07 0x185600f0


/sys/class/sound/hwC1D0/driver_pin_configs:


/sys/class/sound/hwC1D0/user_pin_configs:


/sys/class/sound/hwC1D0/init_verbs:


/sys/class/sound/hwC1D0/hints:




!!ALSA/HDA dmesg
!!--------------


[   16.038026] ieee80211 phy0: Atheros AR9300 Rev:3 mem=0xffffc90012d00000, irq=19
[   16.094561] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   16.094670] snd_hda_intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[   16.140728] SKU: Nid=0x1d sku_cfg=0x4007e619
--
[   16.141192] realtek: Enabling init ASM_ID=0xe619 CODEC_ID=10ec0899
[   16.152478] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   16.152585] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   16.152696] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.152774] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.152818] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.152855] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.152891] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.153043] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[   16.153087] hda_intel: Disabling MSI
[   16.153092] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.153123] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   16.156351] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   16.640690] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   16.641568] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   16.641640] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   16.641706] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[   16.775255] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X

```

---

### Post by tgalati4 on 2014-02-11
You have two sound cards on this system.  I think what is happening is that the Intel HDA motherboard sound driver is loaded but the nVidia driver (through HDMI) has hooked into the sound system.  So first try turning off your motherboard sound in BIOS then try the sound through your HDMI connection.

---

### Post by juliushibert63 on 2014-02-12
> **tgalati4 said:**
> You have two sound cards on this system.  I think what is happening is that the Intel HDA motherboard sound driver is loaded but the nVidia driver (through HDMI) has hooked into the sound system.  So first try turning off your motherboard sound in BIOS then try the sound through your HDMI connection.

Very interesting. I went into my BIOS and switched off the internal audio control, then rebooted into linux and ran aplay -l and as expected just one sound card was listed (NVidia [HDA NVidia]). Admittedly no sound output was listed in the System Prefs>Audio window. 

Unfortunately I don't have any speakers that can receive output via HDMI. My current screen is an Dell LCD connected to the PCIe Geforce 660 txi card via DVI. 

Is there anyway of getting round this and testing if this HDMI is the problem? The only solution I can think of is to remove the dedicated graphics card and try running the screen straight from the motherboard/cpu integrated HD4000 graphics chip and seeing if audio works, with the dedicated graphics card taken out of the equation.

---

### Post by tgalati4 on 2014-02-12
Yes, unfortunately that is what I would try.  And I expect it will work out-of-the-box.  But just to make sure your Intel sound is working, I would try this test.  I find it strange that you are using DVI and yet the HDMI sound is active.  Are you using a proprietary nVidia driver?  If so swich to the open source driver and see if that narrows it down.  Ideally, you should be able to have all sound channels active and be able to select between them in various applications.  I think we can get there, but it will require some more digging.

Go find an HDMI TV or buy a long HDMI cable and test the HDMI sound through the TV.

---

### Post by juliushibert63 on 2014-02-15
> **tgalati4 said:**
> Yes, unfortunately that is what I would try.  And I expect it will work out-of-the-box.  But just to make sure your Intel sound is working, I would try this test.  I find it strange that you are using DVI and yet the HDMI sound is active.  Are you using a proprietary nVidia driver?  If so swich to the open source driver and see if that narrows it down.  Ideally, you should be able to have all sound channels active and be able to select between them in various applications.  I think we can get there, but it will require some more digging.

Go find an HDMI TV or buy a long HDMI cable and test the HDMI sound through the TV.

So I think we're on to something. I connected the computer up to the LED Screen in my lounge via HDMI and was able to get sound through the TV via HDMI. In order to get sound from the GFX card over HDMI I did have to go into the BIOS and disable the integrated HD4000 graphics chip (I also tried disabling the onboard audio chip too, though this didn't make any difference to sound via the GFX HDMI, both on and off produced sound). 

I also tried completely removing the GFX card and running the screen via the onboard graphics HD4000 again over HDMI. Oddly the HDMI produced sound but the onboard sound again wouldn't produce anything other than just low background noise (which has been the case consistently with all the configurations I've tried). I also tried using the digital out SPDIF (both with and without the GFX card and still no output, not even an indication of the red light on the end of the digital cable that you normally get when a device is outputting digital audio). 

I'm very puzzled.

---

### Post by tgalati4 on 2014-02-15
It is time to *decompose*.  Not rot, but break the problem down into smaller parts and focus on getting one part to work at a time.
Pull the GFX card (no games for you!) and focus on the on-board Intel sound.  Some SPDIF info in Step 15:  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Once that is working then pick another small problem to work.  Otherwise you will pull your hair out trying to solve problems that are confounded by having 2 sound cards.

---

### Post by juliushibert63 on 2014-02-16
> **tgalati4 said:**
> It is time to *decompose*.  Not rot, but break the problem down into smaller parts and focus on getting one part to work at a time.
Pull the GFX card (no games for you!) and focus on the on-board Intel sound.  Some SPDIF info in Step 15:  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Once that is working then pick another small problem to work.  Otherwise you will pull your hair out trying to solve problems that are confounded by having 2 sound cards.

Sorry I think I'd confused things. I'd merely tested the SPDIF as I have a amp attached to my TV that can accept digital audio. However this isn't the case where the computer sits normally. Getting the sound to work on the normal 3.5mm ports is the real problem I'm trying to sort.

After removing the GFX card permanently have you got any other suggestions I could try to get sound to come out of the usual green mobo sound output port?

---

### Post by Yellow Pasque on 2014-02-16
You could update to latest kernel module (you need lts-saucy package): [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

If that doesn't work after rebooting, report a bug:
```
ubuntu-bug audio
```
Since you're using Precise, you should run alsa info again, and give the link on the bug report.

---

### Post by tgalati4 on 2014-02-16
With only on-board sound, you now need to make sure the sound card is turned on in BIOS and go through the troubleshooting steps in the link I posted previously.  Intel HDA sound tends to work without problems, so if you are still having issues, then perhaps file a bug as suggested by Temujin.

---

