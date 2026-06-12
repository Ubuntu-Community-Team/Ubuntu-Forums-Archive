---
title: "Can't mount 2Tb SATA drive"
date: 2018-04-07
forum: Hardware
---

### Post by escuta on 2018-04-07
Hi Forum,

I am unable to mount auxiliary 2Tb SATA drive on my linux machine. The motherboard is an Asus P8Z68-M Pro and the BIOS version is 0402. I am able to mount 1Tb drives with no problems.

I've tried various different SATA ports on the on the mother board and a number of SATA cables to no avail. I've also swapped the drive twice at the shop. One return they tested and found no fault, the second they tested di show a fault. It is possible that the whole batch of drives is faulty I suppose...

"sudo fdisk -l" shows only the master drive and not the second disk:

```
Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xdd82f21f

Dispositivo Inicializar      Start        Fim    Setores   Size Id Tipo
/dev/sdb1   *                 2048 1928396799 1928394752 919,5G 83 Linux
/dev/sdb2               1928398846 1953523711   25124866    12G  5 Estendida
/dev/sdb5               1928398848 1953523711   25124864    12G 82 Linux swap /
```

lspci returns:

```
[COLOR=#242729][FONT=Consolas]00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)[/FONT][/COLOR]00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)
05:01.0 Multimedia audio controller: Xilinx Corporation RME Hammerfall DSP (rev 11)
06:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01) [COLOR=#242729][FONT=Consolas]07:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller[/FONT][/COLOR]
```

lsscsi returns:

```
[COLOR=#242729][FONT=Consolas][2:0:0:0] disk ATA ST2000DM006 CC26 /dev/sda[/FONT][/COLOR][3:0:0:0] cd/dvd HL-DT-ST DVDRAM GH22NS70 EX01 /dev/sr0 [COLOR=#242729][FONT=Consolas][4:0:0:0] disk ATA ST1000NM0011 SN03 /dev/sdb[/FONT][/COLOR]
```

I've posted the latest dmesg printout to: [http://jmp.sh/shvbsTb](http://jmp.sh/shvbsTb)

Can anyone please help?

Thanks

---

### Post by oldfred on 2018-04-07
Do not use Asmedia ports, even for DVD.

Others have posted this:
 Asrock Extreme4 Z77 motherboard, which has 4 SATA3 ports: 2 Intel ports (0 & 1) and 2 Asmedia ports (A0 & A1).Had my DVD drive connected to one of the Asmedia ports (A1), and so I tried switching the connection to one of the Intel SATA2 ports and the errors went away. 


 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564) 
      
 UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
[http://www.asrock.com/mb/Intel/Z77%20Pro3/?cat=Manual](http://www.asrock.com/mb/Intel/Z77%20Pro3/?cat=Manual)

---

