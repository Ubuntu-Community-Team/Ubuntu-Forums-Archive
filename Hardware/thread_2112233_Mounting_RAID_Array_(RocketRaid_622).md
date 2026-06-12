---
title: "Mounting RAID Array (RocketRaid 622)"
date: 2013-02-04
forum: Hardware
---

### Post by bjforesthowell on 2013-02-04
I've got a SansDigital TowerRAID TR8M-B tower, with a RocketRAID 622 eSATA controller that I've ben rocking out with for about a year now. It's been working great until I upgraded to 13.04. I've got 16tb of drive space formated to ext4 running RAID 5.

I'm able to get the drivers installed by following the directions on this site. While using the 3.5.0-23 KERNEL.

[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

I'm even able to get the RAID web gui installed without a problem. Managing the array with this goes off without a hitch.

I see that during the bios setting utility during boot up that the array comes up normal, and I can even see the array when I do a fdisk -l. When I do a lspci I can even see the RAID bus controller.

The only time I'm running into problems recently is when I actually try to mount the drive. My system just freezes up. I've tried to edit my /etc/fstab so that it mounts the array automatically during boot, and this causes my system to crash. If I select noauto then my machine freezes up when I try to mount after log in.

When I don't have an entry in my /etc/fstab file my system keeps trying to create a directory in /media that's different from the UUID.

I'm not saying that it hasn't worked since I went to 13.04, it has worked intermittantly. When it does work I don't have any issues at all with it. I'm hoping someone is going to have some insight to what I've got going on so that I don't just have a paperweight sitting next to my machine any more.





root@GOMI:/dev# lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1c.6 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 7 (rev c4)
00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF110 [GeForce GTX 570] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF110 High Definition Audio Controller (rev a1)
03:00.0 RAID bus controller: HighPoint Technologies, Inc. RocketRAID 622 2 Port SATA-III Controller (rev 01)
03:00.1 IDE interface: Marvell Technology Group Ltd. 88SE9128 IDE Controller (rev 11)
04:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
05:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
07:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
08:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
root@GOMI:/dev#

yoda@GOMI:~$ sudo blkid
[sudo] password for yoda: 
/dev/sda1: UUID="0ae7f721-0b5d-4496-8e57-af6db31f772e" TYPE="ext4" 
/dev/sda5: UUID="a1aba853-3b1e-449b-a905-b0d064452aa0" TYPE="swap" 
/dev/sdb1: LABEL="System Reserved" UUID="20C81A2CC81A00A8" TYPE="ntfs" 
/dev/sdb2: UUID="EC58231B5822E454" TYPE="ntfs" 
/dev/sdc: UUID="aa8dab13-39ed-4e39-8503-653e9a0b38c9" TYPE="ext4" 
yoda@GOMI:~$

root@GOMI:/home/yoda# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=0ae7f721-0b5d-4496-8e57-af6db31f772e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a1aba853-3b1e-449b-a905-b0d064452aa0 none            swap    sw              0       0
# RAID ARRAY
/dev/sdc /media/yoda/aa8dab13-39ed-4e39-8503-653e9a0b38c9 ext4    noauto,rw,user         0       0
root@GOMI:/home/yoda#

root@GOMI:/home/yoda# fdisk -l

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009dc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    91584511    45791232   83  Linux
/dev/sda2        91586558   125044735    16729089    5  Extended
/dev/sda5        91586560   125044735    16729088   82  Linux swap / Solaris

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66caf46d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   125042687    62417920    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 14002.2 GB, 14002197364736 bytes
255 heads, 63 sectors/track, 1702336 cylinders, total 27348041728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x733a288c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           0           0           0    0  Empty
root@GOMI:/home/yoda#

root@GOMI:/media/yoda# ls
aa8dab13-39ed-4e39-8503-653e9a0b38c9  aa8dab13-39ed-4e39-8503-653e9a0b38c91
root@GOMI:/media/yoda#

---

