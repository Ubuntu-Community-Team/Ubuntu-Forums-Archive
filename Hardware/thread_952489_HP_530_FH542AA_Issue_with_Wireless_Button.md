---
title: "HP 530 FH542AA Issue with Wireless Button"
date: 2008-10-19
forum: Hardware
---

### Post by matzumoto on 2008-10-19
Hi there, 

Have an issue with the wireless radio button on my laptop (see subj.), 
the problem is - it doesn't get lighted/un-lighted when is switched on/off.
BUT :  despite on this issue an network connection is activated/deactivated appropriately.

WTF ?? 

Thanks, Artem

P.S. If it helps my log entries are as follows :
[/var/log/messages:]

............................

Oct 19 11:34:34 playstation kernel: [  428.138240] iwl3945: Radio Frequency Kill Switch is On:
Oct 19 11:34:34 playstation kernel: [  428.138246] Kill switch must be turned off for wireless networking to work.
Oct 19 11:36:36 playstation kernel: [  550.308699] iwl3945: Radio Frequency Kill Switch is On:
Oct 19 11:36:36 playstation kernel: [  550.308705] Kill switch must be turned off for wireless networking to work.

[/var/log/syslog:]

...........................

Oct 18 12:57:52 playstation dhcdbd: Started up.
Oct 18 12:57:53 playstation NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/ipw_wlan_switch 
Oct 18 12:57:53 playstation NetworkManager: <info>  eth0: Device is fully-supported using driver 'e100'. 
Oct 18 12:57:53 playstation NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 18 12:57:53 playstation NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 18 12:57:53 playstation NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 18 12:57:53 playstation NetworkManager: <info>  Deactivating device eth0. 
Oct 18 12:57:53 playstation NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 18 12:57:53 playstation NetworkManager: <debug> [1224323873.915295] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7530B'). 
Oct 18 12:57:53 playstation NetworkManager: <info>  Wireless now enabled by radio killswitch 
Oct 18 12:57:56 playstation avahi-daemon[5298]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.5.221.
Oct 18 12:57:56 playstation avahi-daemon[5298]: New relevant interface wlan0.IPv4 for mDNS.
Oct 18 12:57:56 playstation avahi-daemon[5298]: Registering new address record for 169.254.5.221 on wlan0.IPv4.

...............

Oct 18 22:42:31 playstation kernel: [  685.351610] iwl3945: Radio Frequency Kill Switch is On:
Oct 18 22:42:31 playstation kernel: [  685.351616] Kill switch must be turned off for wireless networking to work.
Oct 18 22:42:35 playstation NetworkManager: <info>  Wireless now disabled by radio killswitch 
Oct 18 22:42:41 playstation NetworkManager: <info>  Wireless now enabled by radio killswitch 

[/var/log/kern.log:]

........................

Oct 18 12:57:51 playstation kernel: [   28.516589] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Oct 18 12:57:51 playstation kernel: [   28.516594] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Oct 18 12:57:51 playstation kernel: [   28.526732] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Oct 18 12:57:51 playstation kernel: [   28.526749] PCI: Setting latency timer of device 0000:10:00.0 to 64
Oct 18 12:57:51 playstation kernel: [   28.526779] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Oct 18 12:57:51 playstation kernel: [   29.315768] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
Oct 18 12:57:51 playstation kernel: [   29.316181] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

....................

Oct 18 12:57:51 playstation kernel: [   32.100105] wlan0: Initial auth_alg=0
Oct 18 12:57:51 playstation kernel: [   32.100115] wlan0: authenticate with AP 00:18:39:2c:57:0e
Oct 18 12:57:51 playstation kernel: [   32.101694] wlan0: RX authentication from 00:18:39:2c:57:0e (alg=0 transaction=2 status=0)
Oct 18 12:57:51 playstation kernel: [   32.101700] wlan0: authenticated
Oct 18 12:57:51 playstation kernel: [   32.101705] wlan0: associate with AP 00:18:39:2c:57:0e
Oct 18 12:57:51 playstation kernel: [   32.103383] wlan0: RX AssocResp from 00:18:39:2c:57:0e (capab=0x401 status=0 aid=1)
Oct 18 12:57:51 playstation kernel: [   32.103389] wlan0: associated

---

