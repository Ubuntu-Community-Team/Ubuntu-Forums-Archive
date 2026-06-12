---
title: "Ubuntu 17.04 does not see SD card"
date: 2017-05-06
forum: Hardware
---

### Post by hark781 on 2017-05-06
[COLOR=#000000][COLOR=#000000]17.04 installed Ubuntu on a netbook Acer Aspire One AO756-877B1bb a problem is detected the memory card into a reader sees. And Windows 8.1 sees and reads. [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]The output necessary information.[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]uname -a
[/COLOR][/COLOR][COLOR=#000000]Code:
[COLOR=#000000]
[COLOR=#000000]Linux hark781-AO756 4.10.0-21-generic #23-Ubuntu SMP Fri Apr 28 16:14:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux[/COLOR][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]

[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]lspci
[/COLOR][/COLOR][COLOR=#000000]Code:
[COLOR=#000000]
[COLOR=#000000]hark781@hark781-AO756:~$ lspci[/COLOR]
[COLOR=#000000]00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)[/COLOR]
[COLOR=#000000]00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)[/COLOR]
[COLOR=#000000]00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)[/COLOR]
[COLOR=#000000]00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)[/COLOR]
[COLOR=#000000]00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)[/COLOR]
[COLOR=#000000]00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)[/COLOR]
[COLOR=#000000]00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)[/COLOR]
[COLOR=#000000]00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)[/COLOR]
[COLOR=#000000]00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)[/COLOR]
[COLOR=#000000]00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)[/COLOR]
[COLOR=#000000]00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)[/COLOR]
[COLOR=#000000]00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)[/COLOR]
[COLOR=#000000]03:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)[/COLOR]
[COLOR=#000000]04:00.0 Ethernet controller: Broadcom Limited NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)[/COLOR]
[COLOR=#000000]04:00.1 SD Host controller: Broadcom Limited BCM57765/57785 SDXC/MMC Card Reader (rev 10)[/COLOR][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]

[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]lsusb
[/COLOR][/COLOR][COLOR=#000000]Code:
[COLOR=#000000]
[COLOR=#000000]hark781@hark781-AO756:~$ lsusb[/COLOR]
[COLOR=#000000]Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse[/COLOR]
[COLOR=#000000]Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 001 Device 004: ID 064e:e330 Suyin Corp. [/COLOR]
[COLOR=#000000]Bus 001 Device 005: ID 0489:e04e Foxconn / Hon Hai [/COLOR]
[COLOR=#000000]Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]

[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]dmesg | tail
[/COLOR][/COLOR][COLOR=#000000]Code:
[COLOR=#000000]
[COLOR=#000000]hark781@hark781-AO756:~$ dmesg | tail[/COLOR]
[COLOR=#000000][ 2719.773466] sdhci: Power: 0x0000000f | Blk gap: 0x00000000[/COLOR]
[COLOR=#000000][ 2719.773472] sdhci: Wake-up: 0x00000000 | Clock: 0x0000e8c7[/COLOR]
[COLOR=#000000][ 2719.773478] sdhci: Timeout: 0x00000000 | Int stat: 0x00000000[/COLOR]
[COLOR=#000000][ 2719.773483] sdhci: Int enab: 0x00ff0083 | Sig enab: 0x00ff0083[/COLOR]
[COLOR=#000000][ 2719.773489] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000[/COLOR]
[COLOR=#000000][ 2719.773494] sdhci: Caps: 0x176ec8b0 | Caps_1: 0x03002177[/COLOR]
[COLOR=#000000][ 2719.773499] sdhci: Cmd: 0x0000341a | Max curr: 0x00000000[/COLOR]
[COLOR=#000000][ 2719.773503] sdhci: Host ctl2: 0x00000000[/COLOR]
[COLOR=#000000][ 2719.773510] sdhci: ADMA Err: 0x00000000 | ADMA Ptr: 0x0000000000000000[/COLOR]
[COLOR=#000000][ 2719.773511] sdhci: ===========================================[/COLOR][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]

[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]sudo lshw -short

[/COLOR][/COLOR][COLOR=#000000]Code:
[COLOR=#000000]hark781@hark781-AO756:~$ sudo lshw -short[/COLOR]
[COLOR=#000000][sudo] &#1087;&#1072;&#1088;&#1086;&#1083;&#1100; &#1076;&#1083;&#1103; hark781: [/COLOR]
[COLOR=#000000]H/W path &#1059;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#1050;&#1083;&#1072;&#1089;&#1089; &#1054;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;[/COLOR]
[COLOR=#000000]================================================== ====================[/COLOR]
[COLOR=#000000]system AO756 (AO756_0742_V2.21)[/COLOR]
[COLOR=#000000]/0 bus Mimic[/COLOR]
[COLOR=#000000]/0/0 memory 128KiB BIOS[/COLOR]
[COLOR=#000000]/0/4 processor Intel(R) Celeron(R) CPU 88[/COLOR]
[COLOR=#000000]/0/4/9 memory 32KiB L1 &#1082;&#1101;&#1096;[/COLOR]
[COLOR=#000000]/0/4/a memory 256KiB L2 &#1082;&#1101;&#1096;[/COLOR]
[COLOR=#000000]/0/4/b memory 2MiB L3 &#1082;&#1101;&#1096;[/COLOR]
[COLOR=#000000]/0/8 memory 32KiB L1 &#1082;&#1101;&#1096;[/COLOR]
[COLOR=#000000]/0/18 memory 3GiB &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1085;&#1072;&#1103; &#1087;[/COLOR]
[COLOR=#000000]/0/18/0 memory 1GiB SO-DIMM DDR3 &#1057;&#1080;&#1085;&#1093;[/COLOR]
[COLOR=#000000]/0/18/1 memory 2GiB SO-DIMM DDR3 &#1057;&#1080;&#1085;&#1093;[/COLOR]
[COLOR=#000000]/0/100 bridge 2nd Generation Core Proces[/COLOR]
[COLOR=#000000]/0/100/2 display 2nd Generation Core Proces[/COLOR]
[COLOR=#000000]/0/100/16 communication 7 Series/C216 Chipset Fami[/COLOR]
[COLOR=#000000]/0/100/1a bus 7 Series/C216 Chipset Fami[/COLOR]
[COLOR=#000000]/0/100/1a/1 usb1 bus EHCI Host Controller[/COLOR]
[COLOR=#000000]/0/100/1a/1/1 bus Integrated Rate Matching H[/COLOR]
[COLOR=#000000]/0/100/1a/1/1/1 communication &#1041;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1081; &#65533;[/COLOR]
[COLOR=#000000]/0/100/1a/1/1/3 multimedia HD WebCam[/COLOR]
[COLOR=#000000]/0/100/1b multimedia 7 Series/C216 Chipset Fami[/COLOR]
[COLOR=#000000]/0/100/1c bridge 7 Series/C216 Chipset Fami[/COLOR]
[COLOR=#000000]/0/100/1c.1 bridge 7 Series/C210 Series Chips[/COLOR]
[COLOR=#000000]/0/100/1c.1/0 wlp3s0 network AR9462 Wireless Network Ad[/COLOR]
[COLOR=#000000]/0/100/1c.2 bridge 7 Series/C210 Series Chips[/COLOR]
[COLOR=#000000]/0/100/1c.2/0 enp4s0f0 network NetLink BCM57785 Gigabit E[/COLOR]
[COLOR=#000000]/0/100/1c.2/0.1 generic BCM57765/57785 SDXC/MMC Ca[/COLOR]
[COLOR=#000000]/0/100/1d bus 7 Series/C216 Chipset Fami[/COLOR]
[COLOR=#000000]/0/100/1d/1 usb2 bus EHCI Host Controller[/COLOR]
[COLOR=#000000]/0/100/1d/1/1 bus Integrated Rate Matching H[/COLOR]
[COLOR=#000000]/0/100/1d/1/1/3 input USB OPTICAL MOUSE[/COLOR]
[COLOR=#000000]/0/100/1f bridge 7 Series Chipset Family LP[/COLOR]
[COLOR=#000000]/0/100/1f.2 storage 7 Series Chipset Family 6-[/COLOR]
[COLOR=#000000]/0/100/1f.3 bus 7 Series/C216 Chipset Fami[/COLOR]
[COLOR=#000000]/0/1 scsi0 storage [/COLOR]
[COLOR=#000000]/0/1/0.0.0 /dev/sda disk 120GB KINGSTON SUV400S[/COLOR]
[COLOR=#000000]/0/1/0.0.0/1 /dev/sda1 volume 511MiB Windows FAT volume[/COLOR]
[COLOR=#000000]/0/1/0.0.0/2 /dev/sda2 volume 111GiB &#1058;&#1086;&#1084; EXT4[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]

P.S. Sorry translate english. [/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]Thank you for understanding[/COLOR][/COLOR]

---

