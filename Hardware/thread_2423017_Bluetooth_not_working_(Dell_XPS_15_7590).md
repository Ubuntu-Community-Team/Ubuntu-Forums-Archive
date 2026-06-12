---
title: "Bluetooth not working (Dell XPS 15 7590)"
date: 2019-07-16
forum: Hardware
---

### Post by hanyangx on 2019-07-16
Hello all,

I just got my XPS 15 7590 last week and I am now trying to set up ubuntu 16.04 on it as dual boot. 

The wifi did not work at the beginning and I found a solution here [https://support.killernetworking.com/knowledge-base/killer-ax1650-in-debian-ubuntu-16-04/](https://support.killernetworking.com/knowledge-base/killer-ax1650-in-debian-ubuntu-16-04/) This is because XPS 15 7590 is using Killer AX1650 chipset.

After I followed the instructions above, the WIFI works, but the Bluetooth not. 

This is the information I got by ```
rfkill list
```
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no



```

This is after running ```
lsusb 

lspci
```
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 001 Device 004: ID 27c6:5395  
Bus 001 Device 003: ID 8087:0029 Intel Corp. 
Bus 001 Device 005: ID 0c45:6723 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Device 3e9b
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 07)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:15.0 Serial bus controller [0c80]: Intel Corporation Device a368 (rev 10)
00:15.1 Serial bus controller [0c80]: Intel Corporation Device a369 (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:17.0 SATA controller: Intel Corporation Device a353 (rev 10)
00:1b.0 PCI bridge: Intel Corporation Device a340 (rev f0)
00:1c.0 PCI bridge: Intel Corporation Device a338 (rev f0)
00:1c.4 PCI bridge: Intel Corporation Device a33c (rev f0)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port 9 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device a30e (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
01:00.0 3D controller: NVIDIA Corporation Device 1f91 (rev a1)
3b:00.0 Network controller: Intel Corporation Device 2723 (rev 1a)
3c:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
3d:00.0 Non-Volatile memory controller: Toshiba America Info Systems Device 011a




```
 
And also,

```
 dmesg | grep -i blue
[    3.830702] Bluetooth: Core ver 2.22
[    3.830712] Bluetooth: HCI device and connection manager initialized
[    3.830714] Bluetooth: HCI socket layer initialized
[    3.830715] Bluetooth: L2CAP socket layer initialized
[    3.830717] Bluetooth: SCO socket layer initialized
[    3.982311] Bluetooth: hci0: Bootloader revision 0.3 build 0 week 24 2017
[    3.983577] Bluetooth: hci0: Device revision is 1
[    3.983578] Bluetooth: hci0: Secure boot is enabled
[    3.983578] Bluetooth: hci0: OTP lock is enabled
[    3.983579] Bluetooth: hci0: API lock is enabled
[    3.983579] Bluetooth: hci0: Debug lock is disabled
[    3.983580] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    3.983720] bluetooth hci0: Direct firmware load for intel/ibt-20-1-3.sfi failed with error -2
[    3.983721] Bluetooth: hci0: Failed to load Intel firmware file (-2)
[    3.985641] Bluetooth: hci0: Bootloader revision 0.3 build 0 week 24 2017
[    3.987488] Bluetooth: hci0: Device revision is 1
[    3.987489] Bluetooth: hci0: Secure boot is enabled
[    3.987489] Bluetooth: hci0: OTP lock is enabled
[    3.987490] Bluetooth: hci0: API lock is enabled
[    3.987490] Bluetooth: hci0: Debug lock is disabled
[    3.987491] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[    3.987513] bluetooth hci0: Direct firmware load for intel/ibt-20-1-3.sfi failed with error -2
[    3.987514] Bluetooth: hci0: Failed to load Intel firmware file (-2)
[    4.806487] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.806488] Bluetooth: BNEP filters: protocol multicast
[    4.806490] Bluetooth: BNEP socket layer initialized




```

I noticed that there is "[COLOR=#000000][FONT=&amp]hci0: Direct firmware load for intel/ibt-20-1-3.sfi failed with error -2[/FONT][/COLOR]" but I have no idea what it is.

For hciconfig I got these,
```

hciconfig -a

hci0:    Type: BR/EDR  Bus: USB    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:86 acl:0 sco:0 events:4 errors:0
    TX bytes:12 acl:0 sco:0 commands:4 errors:0
    Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
    Packet type: DM1 DH1 HV1 
    Link policy: 
    Link mode: SLAVE ACCEPT 



```

Anyone has some ideas?

Thanks very much! 

By the way, I've got my kernel version is:
```

uname -a
Linux han-XPS-15-7590 4.15.0-54-generic #58~16.04.1-Ubuntu SMP Mon Jun 24 13:21:41 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

---

