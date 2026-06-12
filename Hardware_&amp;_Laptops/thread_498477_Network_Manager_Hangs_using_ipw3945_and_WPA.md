---
title: "Network Manager Hangs using ipw3945 and WPA"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by Enyo on 2007-07-11
I have a Samsung Q45 with a Intel Pro Wireless 3945 Card using the packaged drivers in fiesty. The system is with fully updated packages.

I can connect to none WPA networks just fine however when I attempt to connect to a network protected with WPA network manager appears to hang (the animation still continues but nothing ever happens).

Can anybody please offer some advice on how to troubleshoot this issue?
```

[ 22.156000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[ 22.156000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[ 22.156000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[ 24.072000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

```
daemon.log --:
```

Jul 11 12:40:51 river NetworkManager: <debug info>^I[1184154051.901162] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'WLAN-A'
Jul 11 12:40:51 river NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth1 / WLAN-A
Jul 11 12:40:51 river NetworkManager: <information>^IDeactivating device eth1.
Jul 11 12:40:51 river NetworkManager: <information>^IDevice eth1 activation scheduled...
Jul 11 12:40:51 river NetworkManager: <information>^IDeactivating device eth0.
Jul 11 12:40:51 river dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 5973
Jul 11 12:40:51 river dhclient: killed old client process, removed PID file
Jul 11 12:40:51 river dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jul 11 12:40:51 river avahi-daemon[5050]: Withdrawing address record for 192.168.1.185 on eth0.
Jul 11 12:40:51 river avahi-daemon[5050]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.185.
Jul 11 12:40:51 river avahi-daemon[5050]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 11 12:40:51 river avahi-autoipd(eth0)[6310]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jul 11 12:40:51 river avahi-autoipd(eth0)[6310]: Successfully called chroot().
Jul 11 12:40:51 river avahi-autoipd(eth0)[6310]: Successfully dropped root privileges.
Jul 11 12:40:51 river avahi-autoipd(eth0)[6310]: fopen() failed: Permission denied
Jul 11 12:40:51 river avahi-autoipd(eth0)[6310]: Starting with address 169.254.8.135
Jul 11 12:40:52 river avahi-daemon[5050]: Withdrawing address record for fe80::213:77ff:fe38:94e9 on eth0.
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) started...
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started...
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1/wireless): access point 'WLAN-A' is encrypted, but NO valid key exists. New key needed.
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) New wireless user key requested for network 'WLAN-A'.
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) New wireless user key for network 'WLAN-A' received.
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started...
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete.
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting...
Jul 11 12:40:52 river NetworkManager: <information>^IActivation (eth1/wireless): access point 'WLAN-A' is encrypted, and a key exists. No new key needed.
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant^I'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: response was 'OK'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: sending command 'AP_SCAN 2'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: response was 'OK'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: response was '0'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 574c414e2d41'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: response was 'OK'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 scan_ssid 1'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: response was 'OK'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 proto WPA'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: response was 'OK'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: response was 'OK'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 psk <key>'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: response was 'OK'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0'
Jul 11 12:40:53 river NetworkManager: <information>^ISUP: response was 'OK'
Jul 11 12:40:53 river NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete.
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Global control interface '/var/run/wpa_supplicant-global'
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RX global ctrl_iface - hexdump_ascii(len=49):
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): 49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74 INTERFACE_ADD et
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): 68 31 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75 h1__wext_/var/ru
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): 6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74 n/wpa_supplicant
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): 09 _
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth1^I^Iwext^I/var/run/wpa_supplicant^I'
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Initializing interface 'eth1' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' bridge 'N/A'
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Initializing interface (2) 'eth1'
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAPOL: SUPP_PAE entering state DISCONNECTED
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAPOL: KEY_RX entering state NO_KEY_RECEIVE
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAPOL: SUPP_BE entering state INITIALIZE
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAP: EAP entering state DISABLED
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAPOL: External notification - portEnabled=0
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAPOL: External notification - portValid=0
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): SIOCGIWRANGE: WE(compiled)=21 WE(source)=16 enc_capa=0xf
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): capabilities: key_mgmt 0xf enc 0xf
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WEXT: Operstate: linkmode=1, operstate=5
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): 7
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_set_wpa
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_set_countermeasures
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_set_drop_unencrypted
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Setting scan request: 0 sec 100000 usec
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Added interface eth1
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Wireless event: cmd=0x8b06 len=8
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RX ctrl_iface - hexdump_ascii(len=9):
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): 41 50 5f 53 43 41 4e 20 32 AP_SCAN 2
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RX ctrl_iface - hexdump_ascii(len=11):
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): 41 44 44 5f 4e 45 54 57 4f 52 4b ADD_NETWORK
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: ADD_NETWORK
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RX ctrl_iface - hexdump_ascii(len=31): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: SET_NETWORK id=0 name='ssid'
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: value - hexdump_ascii(len=12): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): ssid - hexdump_ascii(len=6):
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): 57 4c 41 4e 2d 41 WLAN-A
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): e - hexdump_ascii(len=25): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: SET_NETWORK id=0 name='scan_ssid'
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: value - hexdump_ascii(len=1): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): scan_ssid=1 (0x1)
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RX ctrl_iface - hexdump_ascii(len=23): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: SET_NETWORK id=0 name='proto'
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: value - hexdump_ascii(len=3): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): proto: 0x1
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RX ctrl_iface - hexdump_ascii(len=30): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt'
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: value - hexdump_ascii(len=7): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): key_mgmt: 0x2
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RX ctrl_iface - hexdump_ascii(len=82): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: SET_NETWORK id=0 name='psk'
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: value - hexdump_ascii(len=64): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): PSK - hexdump(len=32): [REMOVED]
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RX ctrl_iface - hexdump_ascii(len=16):
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): 45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30 ENABLE_NETWORK 0
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE: ENABLE_NETWORK id=0
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Setting scan request: 0 sec 0 usec
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): State: DISCONNECTED -> SCANNING
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Trying to associate with SSID 'WLAN-A'
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Cancelling scan request
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WPA: clearing own WPA/RSN IE
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Automatic auth_alg selection: 0x1
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): info
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WPA: Set cipher suites based on configuration
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2 proto 1
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WPA: clearing AP WPA IE
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WPA: clearing AP RSN IE
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WPA: using GTK CCMP
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WPA: using PTK CCMP
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WPA: using KEY_MGMT WPA-PSK
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): No keys have been configured - skip key clearing
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_set_drop_unencrypted
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): State: SCANNING -> ASSOCIATING
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WEXT: Operstate: linkmode=-1, operstate=5
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_associate
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Setting authentication timeout: 60 sec 0 usec
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAPOL: External notification - EAP success=0
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAPOL: External notification - EAP fail=0
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAPOL: External notification - portControl=Auto
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE monitor attached - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 33 32 2d 31 30 00
Jul 11 12:40:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Jul 11 12:40:57 river avahi-autoipd(eth0)[6310]: Callout BIND, address 169.254.8.135 on interface eth0
Jul 11 12:40:57 river avahi-daemon[5050]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.135.
Jul 11 12:40:57 river avahi-daemon[5050]: New relevant interface eth0.IPv4 for mDNS.
Jul 11 12:40:57 river avahi-daemon[5050]: Registering new address record for 169.254.8.135 on eth0.IPv4.
Jul 11 12:41:01 river avahi-autoipd(eth0)[6310]: Successfully claimed IP address 169.254.8.135
Jul 11 12:41:01 river avahi-autoipd(eth0)[6310]: fopen() failed: Permission denied
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): =8
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Wireless event: cmd=0x8b1a len=14
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Authentication with 00:00:00:00:00:00 timed out.
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 33 32 2d 31 30 00
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Added BSSID 00:00:00:00:00:00 into blacklist
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): State: ASSOCIATING -> DISCONNECTED
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WEXT: Operstate: linkmode=-1, operstate=5
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): No keys have been configured - skip key clearing
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAPOL: External notification - portEnabled=0
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): EAPOL: External notification - portValid=0
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Setting scan request: 0 sec 0 usec
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): State: DISCONNECTED -> SCANNING
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Trying to associate with SSID 'WLAN-A'
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 33 32 2d 31 30 00
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Cancelling scan request
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): WPA: clearing own WPA/RSN IE
Jul 11 12:41:53 river NetworkManager: <information>^Iwpa_supplicant(6316): Automatic auth_alg selection: 0x1
Jul 11 12:42:53 river NetworkManager: <information>^IActivation (eth1/wireless): association took too long (>120s), failing activation.
Jul 11 12:42:53 river NetworkManager: <information>^IActivation (eth1) failure scheduled...
Jul 11 12:42:53 river NetworkManager: <information>^IActivation (eth1) failed for access point (WLAN-A)
Jul 11 12:42:53 river NetworkManager: <information>^IActivation (eth1) failed.
Jul 11 12:42:53 river NetworkManager: <information>^IDeactivating device eth1.
Jul 11 12:42:53 river NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'.

```

---

