---
title: "Intel WiMAX 6150 Not Working"
date: 2012-05-29
forum: Hardware
---

### Post by SyntheticShield on 2012-05-29
Well Ive been scouring google and the forums here for a solution and so far nothing I have found seems to be working.  So I hope that someone can help out.

I have a Dell17R i7 running Ubuntu 12.04.  It is equipped with the Intel Centrino WiMAX 6150 card.  I took out the hard drive that the laptop came with and installed an SSD and then installed Ubuntu 12.04.  However, before I did that I did fire up Windows and the WiMAX worked there.

Everything suggests that it should work in Ubuntu as according to intel the driver is part of the kernel.  But so far, no joy.

Below is some stuff from terminal commands.  It looks like the system doesnt even know the card is there.

```

iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"[SSID removed by me]"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:13:10:46:26:E7   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:83   Missed beacon:0

eth0      no wireless extensions.

```


```

rfkill list all

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: dell-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```


```

sudo lshw -C network

  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 34
       serial: ac:72:89:3b:0b:4b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-24-generic firmware=18.168.6.1 ip=192.168.1.25 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:51 memory:d1600000-d1601fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 14:fe:b5:be:25:09
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:52 ioport:3000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff

```


```

dmesg | grep iwl

[    6.156023] iwlwifi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.156063] iwlwifi 0000:01:00.0: setting latency timer to 64
[    6.156105] iwlwifi 0000:01:00.0: pci_resource_len = 0x00002000
[    6.156108] iwlwifi 0000:01:00.0: pci_resource_base = ffffc900057b8000
[    6.156111] iwlwifi 0000:01:00.0: HW Revision ID = 0x34
[    6.156407] iwlwifi 0000:01:00.0: irq 51 for MSI/MSI-X
[    6.156540] iwlwifi 0000:01:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[    6.156754] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[    6.173944] iwlwifi 0000:01:00.0: device EEPROM VER=0x71a, CALIB=0x6
[    6.173949] iwlwifi 0000:01:00.0: Device SKU: 0X150
[    6.173951] iwlwifi 0000:01:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    6.174655] iwlwifi 0000:01:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    6.260601] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
[    6.266512] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    6.516371] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[    6.523312] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[    6.608634] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S
[    6.615631] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1

```

```

lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation HM67 Express Chipset Family LPC Controller [8086:1c4b] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008a] (rev 34)
02:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

```


```

lsmod | grep wl

iwlwifi               328352  0 
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211

```


```

lsmod | grep dell
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
wmi                    19256  1 dell_wmi

```


Hopefully all that will help.  I do have Windows XP running in VirtualBox on the same machine and it too sees the WiMAX.  Im not sure wwhat is lacking in Ubuntu but hopefully someone can get me going in the right direction if not already have a solution.  Thanks in advance.

---

