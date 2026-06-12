---
title: "HP DV5000 DVD-RW Help"
date: 2010-05-28
forum: Hardware
---

### Post by gqpolo on 2010-05-28
When I insert a DVD-RW disc in my drive it does not auto mount and I cant figure out how to access it...here is some info that might help I am using Ubuntu 10:

bill@bill-dv5000:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:04.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:04.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:04.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:04.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
bill@bill-dv5000:~$ sudo lshw -C disk
[sudo] password for bill: 
  *-disk                  
       description: ATA Disk
       product: FUJITSU MHV2100A
       vendor: Fujitsu
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0083
       serial: NS91T642BJGP
       size: 93GiB (100GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000bc5bb
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-4084N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: KQ09
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
bill@bill-dv5000:~$

---

### Post by gqpolo on 2010-05-29
It seems that it is DVD+RW and it only happens if the disc isnt finalized

---

