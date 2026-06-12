---
title: "macbook pro 7.1 - unable to mount root fs on block(0,0)"
date: 2010-10-07
forum: Hardware
---

### Post by changsijay on 2010-10-07
> Hi,all

I use Ubuntu maverick RC installed to my macbook pro 13"
it can boot to gnome, and almost everything works.

Now, I am trying to compile a custom kernel on it
I use kernel 2.6.36-rc6 to compile and config file as attached.

I got kernel panic that can not mount root fs,
I wonder if some driver related to SATA controller lacked to build-in.

below are `lspci` info:

> 00:00.0 Host bridge: nVidia Corporation MCP89 HOST Bridge (rev a1)
00:00.1 RAM memory: nVidia Corporation MCP89 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation Device 0d6d (rev a1)
00:01.1 RAM memory: nVidia Corporation Device 0d6e (rev a1)
00:01.2 RAM memory: nVidia Corporation Device 0d6f (rev a1)
00:01.3 RAM memory: nVidia Corporation Device 0d70 (rev a1)
00:02.0 RAM memory: nVidia Corporation Device 0d71 (rev a1)
00:02.1 RAM memory: nVidia Corporation Device 0d72 (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP89 LPC Bridge (rev a2)
00:03.1 RAM memory: nVidia Corporation MCP89 Memory Controller (rev a1)
00:03.2 SMBus: nVidia Corporation MCP89 SMBus (rev a1)
00:03.3 RAM memory: nVidia Corporation MCP89 Memory Controller (rev a1)
00:03.4 Co-processor: nVidia Corporation MCP89 Co-Processor (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP89 OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP89 EHCI USB 2.0 Controller (rev a2)
00:06.0 USB Controller: nVidia Corporation MCP89 OHCI USB 1.1 Controller (rev a1)
00:06.1 USB Controller: nVidia Corporation MCP89 EHCI USB 2.0 Controller (rev a2)
00:08.0 Audio device: nVidia Corporation MCP89 High Definition Audio (rev a2)
00:0a.0 IDE interface: nVidia Corporation MCP89 SATA Controller (rev a2)
00:0b.0 RAM memory: nVidia Corporation Device 0d75 (rev a1)
00:0e.0 PCI bridge: nVidia Corporation Device 0d9a (rev a1)
00:15.0 PCI bridge: nVidia Corporation Device 0d9b (rev a1)
00:16.0 PCI bridge: nVidia Corporation Device 0d9b (rev a1)
00:17.0 PCI bridge: nVidia Corporation MCP89 PCI Express Bridge (rev a1)
01:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 08)
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
04:00.0 VGA compatible controller: nVidia Corporation Device 08a0 (rev a2)

and my partition info
/ on /dev/sda3
swap on /dev/sda4

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       26294   210995460   af  HFS / HFS+
/dev/sda3   *       26310       30200    31250000   83  Linux
/dev/sda4           30217       30385     1355068   82  Linux swap / Solaris

and grub entry as below:

> menuentry 'Ubuntu, with Linux 2.6.36-rc6' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_gpt
        insmod ext2
        set root='(hd0,gpt3)'
        linux   /boot/bzImage root=/dev/sda3 ro reboot=pci
}

I've build-in below options that I am not sure if they are the root cause, but removed they I got the same kernel panic:
>  Device Drivers  --->
<*> Serial ATA and Parallel ATA drivers  --->
<*>   AHCI SATA support
[*]   ATA SFF support 
[*]     ATA BMDMA support
<*>       NVIDIA SATA support 

Could give me some suggestions to try?
thanks

---

