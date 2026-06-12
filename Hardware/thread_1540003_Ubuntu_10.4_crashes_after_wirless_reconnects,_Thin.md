---
title: "Ubuntu 10.4 crashes after wirless reconnects, Thinkpad Edge"
date: 2010-07-27
forum: Hardware
---

### Post by colinkingswood on 2010-07-27
Hi I have installed Ubuntu 10.4 on my Thinkpad Edge 13(AMD) version.

It seems to crash every time the wireless connection drops, then starts to reconnect. (Update not every time, but frequently). 

Here is the output of lspci, and the part of syslog where I think it last happened. 

 lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)


syslog:
ul 27 14:23:02 colin-laptop avahi-daemon[769]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.20.
Jul 27 14:23:02 colin-laptop avahi-daemon[769]: New relevant interface wlan0.IPv4 for mDNS.
Jul 27 14:23:02 colin-laptop avahi-daemon[769]: Registering new address record for 192.168.1.20 on wlan0.IPv4.
Jul 27 14:23:02 colin-laptop dhclient: bound to 192.168.1.20 -- renewal in 6965 seconds.
Jul 27 14:23:02 colin-laptop kernel: [   73.615429] rtllib: TsStartAddBaProcess()==>BA timer is already added
Jul 27 14:23:02 colin-laptop kernel: [   73.652525] ====>to send ADDBAREQ!!!!!
Jul 27 14:23:02 colin-laptop kernel: [   73.657077] ====>rx ADDBARSP from :00:24:36:ab:26:f3
Jul 27 14:23:03 colin-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jul 27 14:23:03 colin-laptop NetworkManager: <info>  Policy set 'Auto GBL-Mac-2' (wlan0) as default for routing and DNS.
Jul 27 14:23:03 colin-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jul 27 14:23:03 colin-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 27 14:23:03 colin-laptop ntpdate[1336]: adjust time server 91.189.94.4 offset 0.213966 sec
Jul 27 14:23:05 colin-laptop kernel: [   77.030112] ====>to send ADDBAREQ!!!!!
Jul 27 14:23:05 colin-laptop kernel: [   77.032341] ====>rx ADDBARSP from :00:24:36:ab:26:f3
Jul 27 14:23:09 colin-laptop kernel: [   80.257775] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 27 14:23:10 colin-laptop kernel: [   81.880354] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 27 14:23:10 colin-laptop kernel: [   82.032525] wlan0: no IPv6 routers present
Jul 27 14:23:49 colin-laptop kernel: [  120.262994] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 27 14:23:50 colin-laptop kernel: [  121.890300] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 27 14:23:58 colin-laptop AptDaemon: INFO: Initializing daemon
Jul 27 14:24:33 colin-laptop kernel: [  164.720123] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 27 14:24:49 colin-laptop kernel: [  180.262476] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 27 14:24:49 colin-laptop kernel: [  180.262668] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 27 14:24:50 colin-laptop kernel: [  181.890357] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 27 14:25:34 colin-laptop kernel: [  225.449455] rtl8192_hw_sleep_down(): RF Change in progress!
Jul 27 14:25:38 colin-laptop kernel: [  229.445064] rtl8192_hw_sleep_down(): RF Change in progress!
Jul 27 14:26:09 colin-laptop kernel: [  260.258713] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 27 14:26:09 colin-laptop kernel: [  260.258896] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 27 14:26:10 colin-laptop kernel: [  261.880285] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 27 14:26:24 colin-laptop kernel: [  275.445682] rtl8192_hw_sleep_down(): RF Change in progress!
Jul 27 14:26:48 colin-laptop kernel: [  299.624277] ========>too long to sleep:8, ffffffda, 3e8
Jul 27 14:26:48 colin-laptop kernel: [  299.726689] ========>too long to sleep:8, ffffffe4, 3e8
Jul 27 14:26:48 colin-laptop kernel: [  299.829100] ========>too long to sleep:8, ffffffee, 3e8
Jul 27 14:27:49 colin-laptop kernel: [  360.257986] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Jul 27 14:27:49 colin-laptop kernel: [  360.258179] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 27 14:27:50 colin-laptop kernel: [  361.890283] ===>rtl8192se_link_change():ieee->iw_mode is 2
Jul 27 14:28:46 colin-laptop kernel: [  417.443199] rtl8192_hw_sleep_down(): RF Change in progress!
Jul 27 14:28:59 colin-laptop AptDaemon: INFO: Quiting due to inactivity
Jul 27 14:28:59 colin-laptop AptDaemon: INFO: Shutdown was requested
Jul 27 14:29:44 colin-laptop wpa_supplicant[883]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul 27 14:29:44 colin-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jul 27 14:29:Jul 27 14:31:34 colin-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.

---

### Post by tvillamil on 2010-07-28
I have a Lenovo T400, and the same thing is happening to me.  Very frustrating.

---

### Post by rCXer on 2010-07-28
Look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/550490"), if you haven't already.  Many others reported problems with wireless in [this]("http://ubuntuforums.org/showthread.php?t=1412406") (really long) thread.  In the thread some people managed to fix this by installing the manufacturer's drivers.

---

### Post by colinkingswood on 2010-08-21
OK, I followed the instructions on [this page]("http://blog.zorinholdings.com/post/501557101/lenovo-thinkpad-edge-wifi-with-ubuntu-10-04"). For some reason the first time I downloaded the driver package I got the wrong one, which just confused me. 

Anyway, I have the drivers installed now, as this page describes. Not used them enough to decide if the crashing still happens, but it is now showing 3 or 4 bars of wireless reception, from a room whee I previously only got one or two. So I guess that is an improvement.

Update:
Yes these drivers are a definite improvement over the standard Ubuntu drivers. Doesn't cause the laptop to crash like the old ones seemed to.

---

