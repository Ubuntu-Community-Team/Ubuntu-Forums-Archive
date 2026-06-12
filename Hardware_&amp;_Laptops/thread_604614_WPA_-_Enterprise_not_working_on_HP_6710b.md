---
title: "WPA - Enterprise not working on HP 6710b"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by iurgi on 2007-11-06
Hi

I was using Ubuntu 7.04 on a IBM (Lenovo) Thinkpad R50e. I had no problems in connecting to the WPA-Enterprise in my office.

I switched to an HP 6710b and now upgraded to ubuntu 7.10. I can't manage to connect to the WPA-Enterprise. But not only that, the NetworkManager seems to be unstable in general: doesn't switch smoothly from one connection to another (actually, it freezes when it can't connect to a signal until it reaches some timeout value or so. I can't even kill it with killall, just with kill -9 pid). If it's trying to connect either to a signal or to a wired connection, and I decide to connect to another one, it just refuses to change until a long time has passed and after that, not always does it.

This is driving me crazy, and is probably the ONLY problem I found so far (apart from the fingerprint reader, that doesn't work yet).

Anyone experiencing this same problem? Any solutions yet?

Find below an output of my syslog when trying to associate to the office signal

Thanks

Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) started... 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1/wireless): access point 'Office' is encrypted, but NO valid key exists.  New key needed. 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Office'. 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Office' received. 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  6 15:56:27 oka NetworkManager: <info>  Activation (eth1/wireless): access point 'Office' is encrypted, and a key exists.  No new key needed. 
Nov  6 15:56:28 oka NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov  6 15:56:28 oka NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant4^I' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was '0' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 464f4e2d4f6666696365' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-EAP' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 eap TTLS' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 identity "iurgi"' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 password <password>' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 client_cert "/home/iurgi/cert.pem"' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ca_cert "/home/iurgi/cert.pem"' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov  6 15:56:28 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:56:28 oka NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  6 15:56:31 oka kernel: [17957.604000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Nov  6 15:56:32 oka NetworkManager: <debug> [1194360992.677139] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:19:07:8E:D9:60 to 00:19:07:92:D9:40 on wireless network 'Office' 
Nov  6 15:56:32 oka NetworkManager: <debug> [1194360992.763138] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Office' 
Nov  6 15:56:32 oka NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  6 15:56:33 oka avahi-daemon[6102]: Registering new address record for fe80::21b:77ff:fe42:57c8 on eth1.*.
Nov  6 15:56:34 oka NetworkManager: <debug> [1194360994.677162] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:19:07:92:D9:40 to 00:19:07:8E:D9:60 on wireless network 'Office' 
Nov  6 15:56:34 oka NetworkManager: <debug> [1194360994.683976] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Office' 
Nov  6 15:56:34 oka NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  6 15:56:42 oka kernel: [17968.304000] eth1: no IPv6 routers present
Nov  6 15:56:46 oka NetworkManager: <debug> [1194361006.678035] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:19:07:8E:D9:60 to 00:19:A9:E2:E5:80 on wireless network 'Office' 
Nov  6 15:56:46 oka NetworkManager: <debug> [1194361006.684557] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Office' 
Nov  6 15:56:46 oka NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  6 15:56:51 oka NetworkManager: <info>  Activation (eth1/wireless): disconnected during association, asking for new key. 
Nov  6 15:56:51 oka NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Office'. 
Nov  6 15:57:10 oka NetworkManager: <debug> [1194361030.683676] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:19:A9:E2:E5:80 to 00:19:07:92:D9:40 on wireless network 'Office' 
Nov  6 15:57:10 oka NetworkManager: <debug> [1194361030.691065] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Office' 
Nov  6 15:57:21 oka NetworkManager: <info>  eth1: link timed out. 
Nov  6 15:57:22 oka NetworkManager: <debug> [1194361042.697109] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:19:07:92:D9:40 to 00:19:07:8E:D9:60 on wireless network 'Office' 
Nov  6 15:57:22 oka NetworkManager: <debug> [1194361042.719456] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Office' 
Nov  6 15:57:30 oka kernel: [18016.404000] ipw3945: association process canceled
Nov  6 15:57:32 oka NetworkManager: <info>  Activation (eth1) New wireless user key for network 'Office' received. 
Nov  6 15:57:32 oka NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  6 15:57:32 oka NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  6 15:57:32 oka NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  6 15:57:32 oka NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  6 15:57:32 oka NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  6 15:57:32 oka NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Nov  6 15:57:32 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:32 oka NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Nov  6 15:57:32 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:32 oka NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Nov  6 15:57:32 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:32 oka NetworkManager: <info>  Activation (eth1/wireless): access point 'Office' is encrypted, and a key exists.  No new key needed. 
Nov  6 15:57:33 oka NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov  6 15:57:33 oka avahi-daemon[6102]: Withdrawing address record for fe80::21b:77ff:fe42:57c8 on eth1.
Nov  6 15:57:33 oka NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant5^I' 
Nov  6 15:57:33 oka kernel: [18019.784000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:33 oka NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was '0' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 464f4e2d4f6666696365' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-EAP' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 eap TTLS' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 identity "iurgi"' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 password <password>' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 client_cert "/home/iurgi/cert.pem"' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov  6 15:57:33 oka NetworkManager: <info>  SUP: response was 'OK' 
Nov  6 15:57:33 oka NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  6 15:57:37 oka NetworkManager: <debug> [1194361057.693174] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:19:07:8E:D9:60 to 00:19:07:92:D9:40 on wireless network 'Office' 
Nov  6 15:57:37 oka NetworkManager: <debug> [1194361057.700133] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Office' 
Nov  6 15:57:37 oka NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  6 15:57:51 oka kernel: [18037.372000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Nov  6 15:57:52 oka avahi-daemon[6102]: Registering new address record for fe80::21b:77ff:fe42:57c8 on eth1.*.
Nov  6 15:57:55 oka NetworkManager: <debug> [1194361075.698290] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:19:07:92:D9:40 to 00:19:07:8E:D9:60 on wireless network 'Office' 
Nov  6 15:57:55 oka NetworkManager: <debug> [1194361075.707045] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Office' 
Nov  6 15:57:55 oka NetworkManager: <info>  Old device 'eth1' activating, won't change. 
Nov  6 15:57:56 oka NetworkManager: <info>  Activation (eth1/wireless): disconnected during association, asking for new key. 
Nov  6 15:57:56 oka NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Office'.

---

