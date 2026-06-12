---
title: "Cannot get Dell XPS gen2 wirelessto work...."
date: 2010-06-30
forum: Hardware
---

### Post by ringding on 2010-06-30
Hi guys,
I have a Dell XPS GEN 2 laptop and I cannot seem to get the wireless to work.

I have tried ndiswrapper...kept freezing the OS (Ubuntu 10.04 upgraded from 9.04).

I can actually turn on and off the switch using the hardware key of Fn + F2.

Here is some info:

My wireless card sees the network I want to connect to with iwlist scan....
~$ **iwlist scan**
Cell 05 - Address: 00:21:E8:C2:05:E8
                    ESSID:"Sprint MiFi2200 5E8 Secure"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=97/100  Signal level=-28 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 4280ms ago

~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


~$ **sudo lshw -C network**
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:e5:13:4d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5705-v3.16 ip=192.168.0.105 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:dcff0000-dcffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
       resources: memory:dcfef000-dcfeffff

~$ **lspci -nn**
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV41.9 [GeForce Go 6800 Ultra] [10de:00c9] (rev a2)
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet [14e4:165e] (rev 03)
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 08)
03:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 17)
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)


~$ **dmesg |grep ipw2200**
[ 1834.194536] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[ 1834.194540] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 1834.194623] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1834.195752] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 1834.195797] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[ 1834.338399] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)


What am I missing?
Any help would be greatly appreciated!

Thanks

---

