---
title: "The problem with SATA controller"
date: 2013-06-14
forum: Hardware
---

### Post by Krovavii on 2013-06-14
Hi, guys!

I have some problems with my SATA controller.

> [    8.581893] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
**[    8.581896] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)**
**[   11.819379] ata1.01: qc timeout (cmd 0xef)**
[   11.819390] ata1.01: failed to enable DIPM, Emask 0x4
[   11.819405] ata1.00: hard resetting link
[   12.138993] ata1.01: hard resetting link
[   12.614501] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[   12.614525] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[   12.638775] ata1.00: configured for UDMA/133
**[   12.654832] ata1.01: configured for UDMA/133**
**[   22.642434] ata1.01: qc timeout (cmd 0xef)**
[   22.642443] ata1.01: failed to enable DIPM, Emask 0x4
[   22.642447] ata1.00: disabling LPM on the link
[   22.642455] ata1.01: limiting SATA link speed to 1.5 Gbps
[   22.642459] ata1.01: limiting speed to UDMA/133:PIO3
[   22.642471] ata1.00: hard resetting link
[   22.962042] ata1.01: hard resetting link
[   23.437541] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[   23.437564] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   23.461892] ata1.00: configured for UDMA/133
[   23.478015] ata1.01: configured for UDMA/133
**[   23.478042] ata1: EH complete**
**[   38.775156] ata1: lost interrupt (Status 0x0)**
[   38.775193] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0 frozen
[   38.775201] ata1.01: failed command: IDENTIFY DEVICE
[   38.775213] ata1.01: cmd ec/00:01:00:00:00/00:00:00:00:00/50 tag 0 pio 512 in
[   38.775213]          res 40/00:01:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[   38.775218] ata1.01: status: { DRDY }
[   38.775232] ata1.00: hard resetting link
[   39.094774] ata1.01: hard resetting link
[   39.570281] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 330)
[   39.570306] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   39.594574] ata1.00: configured for UDMA/133
[   39.610711] ata1.01: configured for UDMA/133
[   39.610750] ata1: EH complete
[   40.510986] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   40.551913] EXT4-fs (sdb3): re-mounted. Opts: commit=600
[   40.612120] init: plymouth-stop pre-start process (2220) terminated with status 1


My laptop has 2 drives: HDD and SSD. I was install Ubuntu 13.04 AMD64 to SSD. In the beginning it was booting for 10-12 seconds. But now it booting 40-50 seconds! 
I was trying to add "libata.noacpi=1" to grub.cfg, but it is useless.
All drivers has not errors at SMARTs data. 

Configuration:
**lspci:**
> 00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 7 Series Chipset Family 4-port SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.5 IDE interface: Intel Corporation 7 Series Chipset Family 2-port SATA Controller [IDE mode] (rev 04)
01:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
01:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)


**cat /etc/fstab**
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=ce420caa-c1b0-4ddf-ace4-7833eb9052e3 /               ext4    errors=remount-ro data=writeback barrier=0 commit=600 0       1
# /home was on /dev/sdb3 during installation
UUID=7a85f059-5514-4d3f-8671-d0927b88044f /home           ext4    defaults        0       2
# /media/windows was on /dev/sdb4 during installation
UUID=6C3878183E2EECAA /media/windows  ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sdb2 during installation
UUID=6bf1934a-e103-46c1-8f56-eb8e19a33df0 none            swap    sw              0       0

**uname -a**
> Linux ubuntu-ultra 3.9.6-030906-generic #201306131535 SMP Thu Jun 13 19:35:54 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

**lshw -html**
[ATTACH]243807[/ATTACH]

Could you help me, please? Thanks!

---

### Post by Yellow Pasque on 2013-06-14
> ata1.01: failed to enable DIPM
If you have the option in BIOS/EFI, you could try disabling power management for the SATA devices. (I'm assuming you're on a desktop where the extra power would be negligible. If you're on a laptop, disabling power management for the device may decrease battery life.)

---

### Post by Krovavii on 2013-06-16
> **Temüjin said:**
> If you have the option in BIOS/EFI, you could try disabling power management for the SATA devices. (I'm assuming you're on a desktop where the extra power would be negligible. If you're on a laptop, disabling power management for the device may decrease battery life.)

Thanks for your help! :)
Unfortunately i can't find this option in BIOS. 
Sometimes "libata.noacpi=1" option helps me to solve problem. But it is strange that it's works only sometimes.

---

### Post by Krovavii on 2013-06-21
Hmm, looks like i know how to solve this. I set SATA to IDE mode when was install OS. Now i change SATA to AHCI mode. I have some problems with booting because i am set a "MODULES=most" to "MODULES=dep" in /etc/initramfs-tools/initramfs.conf. The Kernel doen't load necessary driver and OS is freezing. 
I was turn back this options and was make:


```
sudo update-initramfs -k all -u


```

OS booting normaly after this and errors are gone. :)

---

