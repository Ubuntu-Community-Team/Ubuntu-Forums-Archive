---
title: "Intel 4965AGN Problem"
date: 2010-02-10
forum: Hardware
---

### Post by happyface_0 on 2010-02-10
Hi.
So I installed wicd and replaced gnome's nm-manager. It then stopped working so I removed it and reinstalled nm-manager. nm-manager then didn't display any wifi cards. I could use ifconfig and scan for networks, but couldn't get an IP from them. Since there was a kernel update, I thought drivers would be the issue so I compiled the compat-wireless package; which didn't work. I uninstalled those, and now I have no wifi working (but BT works fine).
Here's some info:
```
dave@dave-ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

dave@dave-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:44:b1:1c
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f1ffc000-f1ffffff ioport:de00(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f1efe000-f1efffff

dave@dave-ubuntu:~$ sudo dmesg|grep 80211
[   26.270259] cfg80211: Calling CRDA to update world regulatory domain
[   26.278177] iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
[   26.278179] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
[   26.278364] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
[   26.278365] iwlcore: Unknown symbol ieee80211_alloc_hw
[   26.278483] iwlcore: disagrees about version of symbol ieee80211_wake_queue
[   26.278485] iwlcore: Unknown symbol ieee80211_wake_queue
[   26.278537] iwlcore: disagrees about version of symbol ieee80211_get_tkip_key
[   26.278538] iwlcore: Unknown symbol ieee80211_get_tkip_key
[   26.278610] iwlcore: disagrees about version of symbol ieee80211_find_sta
[   26.278612] iwlcore: Unknown symbol ieee80211_find_sta
[   26.278706] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   26.278708] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
[   26.278844] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
[   26.278846] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
[   26.278933] iwlcore: Unknown symbol ieee80211_sta_block_awake
[   26.279009] iwlcore: disagrees about version of symbol ieee80211_wake_queues
[   26.279010] iwlcore: Unknown symbol ieee80211_wake_queues
[   26.279125] iwlcore: disagrees about version of symbol ieee80211_stop_queue
[   26.279127] iwlcore: Unknown symbol ieee80211_stop_queue
[   26.279186] iwlcore: disagrees about version of symbol ieee80211_stop_queues
[   26.279187] iwlcore: Unknown symbol ieee80211_stop_queues
[   26.279249] iwlcore: disagrees about version of symbol ieee80211_scan_completed
[   26.279250] iwlcore: Unknown symbol ieee80211_scan_completed
[   26.279459] iwlcore: Unknown symbol ieee80211_beacon_get_tim
[   26.279693] iwlcore: Unknown symbol mac80211_ieee80211_rx
[   26.312255] cfg80211: World regulatory domain updated:

dave@dave-ubuntu:~$ lsmod | grep 80211
mac80211              243496  0 
cfg80211              152616  1 mac80211

dave@dave-ubuntu:~$ lspci|grep 49
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

dave@dave-ubuntu:~$ lsusb|grep com
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. 
dave@dave-ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

dave@dave-ubuntu:~$ sudo lshw -businfo|grep 4965
pci@0000:0b:00.0              network     PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
```

---

### Post by happyface_0 on 2010-02-10
Sorry wrong section, can someone move this?
Thanks

---

### Post by johndoe32102002 on 2010-02-10
Before starting, download the *.deb packages for network-manager, gnome-network-manager, wicd

1.) sudo dpkg --purge network-manager gnome-network-manager wicd
2.) sudo apt-get autoclean && sudo apt-get autoremove
3.) sudo apt-get install network-manager gnome-network-manager

Hope that works; it is clearing the program and configuration and reinstalling.

---

### Post by happyface_0 on 2010-02-12
> **johndoe32102002 said:**
> Before starting, download the *.deb packages for network-manager, gnome-network-manager, wicd

1.) sudo dpkg --purge network-manager gnome-network-manager wicd
2.) sudo apt-get autoclean && sudo apt-get autoremove
3.) sudo apt-get install network-manager gnome-network-manager

Hope that works; it is clearing the program and configuration and reinstalling.

My savior! I don't know why I didn't try this earlier. I thought it was a more in-depth problem. Thanks a lot.

---

### Post by happyface_0 on 2010-02-13
Well this definitely wasn't a permanent fix because network manager doesn't show any wireless card again, but ifconfig does.

---

