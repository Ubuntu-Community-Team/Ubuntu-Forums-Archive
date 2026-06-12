---
title: "bluetooth cann't detect any device ubuntu 16.04"
date: 2017-07-21
forum: Hardware
---

### Post by mquzwini on 2017-07-21
hello guys!! 
i have problem with my fujitsu lifebook t731 bluetooth,it's can not detect and pair with my phone and my headset, it happened after i upgraded to ubuntu 16.04 i guess
note : i try ubuntu 16.04, linux mint (sarah), and now on linux lite and all these distributions have the same problem 
 here is my info
---------------------------------------------------------
ninjago@ninjago-LIFEBOOK-T731:~$ uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
Linux ninjago-LIFEBOOK-T731 4.4.0-85-generic #108-Ubuntu SMP Mon Jul 3 17:23:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Fujitsu Limited. 82579LM Gigabit Network Connection [10cf:161b]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
--
0a:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Fujitsu Limited. AR9287 Wireless Network Adapter (PCI-Express) [10cf:158f]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
Bus 002 Device 005: ID 0489:e031 Foxconn / Hon Hai 
Bus 002 Device 004: ID 056a:00e6 Wacom Co., Ltd 
Bus 002 Device 003: ID 04f2:b169 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 275d:0ba6  
Bus 001 Device 003: ID 08ff:2683 AuthenTec, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   18.607775] Bluetooth: Core ver 2.21
[   18.607823] Bluetooth: HCI device and connection manager initialized
[   18.607827] Bluetooth: HCI socket layer initialized
[   18.607830] Bluetooth: L2CAP socket layer initialized
[   18.607835] Bluetooth: SCO socket layer initialized
[   18.970248] Bluetooth: hci0: BCM: chip id 20
[   18.986240] Bluetooth: hci0: BCM20702A
[   18.986244] Bluetooth: hci0: BCM (001.001.024) build 0000
[   19.298393] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   19.298405] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   23.244565] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.244568] Bluetooth: BNEP filters: protocol multicast
[   23.244571] Bluetooth: BNEP socket layer initialized
[   34.212446] Bluetooth: RFCOMM TTY layer initialized
[   34.212454] Bluetooth: RFCOMM socket layer initialized
[   34.212460] Bluetooth: RFCOMM ver 1.11
[ 2798.441902] Bluetooth: hci0 urb ffff880098178c00 failed to resubmit (2)
[ 2807.193673] Bluetooth: hci0: BCM: chip id 20
[ 2807.209666] Bluetooth: hci0: ninjago-LIFEBOOK-T731
[ 2807.209680] Bluetooth: hci0: BCM (001.001.024) build 0000
[ 2807.209719] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 2807.209726] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[    0.144142] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   19.298393] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 2807.209719] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
bluetooth             520192  39 bnep,btbcm,btrtl,btusb,rfcomm,btintel

---

