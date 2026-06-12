---
title: "Cannot connect to AP after security update."
date: 2008-11-15
forum: Hardware
---

### Post by nathacof on 2008-11-15
I ran the recommended security updates via the update manager, and now my wireless card will not connect to my WEP encrypted AP:

The messages I'm getting from syslog seem to indicate that I am authenticating with the AP:

> Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Activation (ath0/wireless): connection 'Auto sara' has security, and secrets exist.  No new secrets needed. 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Config: added 'ssid' value 'sara' 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN' 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Nov 15 02:48:37 nathacof-laptop kernel: [ 1214.194573] ath0 direct probe responded
Nov 15 02:48:37 nathacof-laptop kernel: [ 1214.194585] ath0: authenticate with AP 00:e0:98:d2:89:f5
Nov 15 02:48:37 nathacof-laptop kernel: [ 1214.195900] ath0: authenticated
Nov 15 02:48:37 nathacof-laptop kernel: [ 1214.195903] ath0: associate with AP 00:e0:98:d2:89:f5
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2 
Nov 15 02:48:37 nathacof-laptop kernel: [ 1214.198668] ath0: RX AssocResp from 00:e0:98:d2:89:f5 (capab=0x461 status=0 aid=1)
Nov 15 02:48:37 nathacof-laptop kernel: [ 1214.198676] ath0: associated
Nov 15 02:48:37 nathacof-laptop kernel: [ 1214.199061] ath0: disassociating by local choice (reason=3)
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 4 
Nov 15 02:48:37 nathacof-laptop NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 0 
Nov 15 02:48:38 nathacof-laptop NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 3 
Nov 15 02:48:39 nathacof-laptop kernel: [ 1216.224063] ath0: authenticate with AP 00:16:b6:21:3e:94
Nov 15 02:48:39 nathacof-laptop kernel: [ 1216.225524] ath0: authenticated
Nov 15 02:48:39 nathacof-laptop kernel: [ 1216.225533] ath0: associate with AP 00:16:b6:21:3e:94
Nov 15 02:48:39 nathacof-laptop NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 4 
Nov 15 02:48:39 nathacof-laptop NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 7 
Nov 15 02:48:39 nathacof-laptop NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'sara'. 
Nov 15 02:48:39 nathacof-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 15 02:48:39 nathacof-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
Nov 15 02:48:39 nathacof-laptop NetworkManager: <info>  (ath0): device state change: 5 -> 7 
Nov 15 02:48:39 nathacof-laptop NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
Nov 15 02:48:39 nathacof-laptop kernel: [ 1216.227547] ath0: RX AssocResp from 00:16:b6:21:3e:94 (capab=0x411 status=0 aid=3)
Nov 15 02:48:39 nathacof-laptop kernel: [ 1216.227554] ath0: associated
Nov 15 02:48:39 nathacof-laptop NetworkManager: <info>  dhclient started with pid 9186 
Nov 15 02:48:39 nathacof-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 15 02:48:39 nathacof-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov 15 02:48:39 nathacof-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov 15 02:48:39 nathacof-laptop dhclient: All rights reserved.
Nov 15 02:48:39 nathacof-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 15 02:48:39 nathacof-laptop dhclient: 
Nov 15 02:48:39 nathacof-laptop dhclient: wmaster0: unknown hardware address type 801
Nov 15 02:48:39 nathacof-laptop NetworkManager: <info>  DHCP: device ath0 state changed normal exit -> preinit 
Nov 15 02:48:39 nathacof-laptop dhclient: wmaster0: unknown hardware address type 801
Nov 15 02:48:39 nathacof-laptop dhclient: Listening on LPF/ath0/00:1f:3a:4d:24:6d
Nov 15 02:48:39 nathacof-laptop dhclient: Sending on   LPF/ath0/00:1f:3a:4d:24:6d
Nov 15 02:48:39 nathacof-laptop dhclient: Sending on   Socket/fallback
Nov 15 02:48:39 nathacof-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
Nov 15 02:48:45 nathacof-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
Nov 15 02:48:56 nathacof-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
Nov 15 02:49:08 nathacof-laptop dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
Nov 15 02:49:24 nathacof-laptop NetworkManager: <info>  Device 'ath0' DHCP transaction took too long (>45s), stopping it. 
Nov 15 02:49:24 nathacof-laptop NetworkManager: <info>  ath0: canceled DHCP transaction, dhcp client pid 9186 
Nov 15 02:49:24 nathacof-laptop NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Nov 15 02:49:24 nathacof-laptop NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) started... 
Nov 15 02:49:24 nathacof-laptop NetworkManager: <info>  Activation (ath0/wireless): could not get IP configuration for connection 'Auto sara'. 
Nov 15 02:49:24 nathacof-laptop NetworkManager: <info>  (ath0): device state change: 7 -> 6 
Nov 15 02:49:24 nathacof-laptop NetworkManager: <info>  Activation (ath0/wireless): asking for new secrets 
Nov 15 02:49:24 nathacof-laptop NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Timeout) complete. 


I'm using the ath5k drivers for my wireless, and this was working in Intrepid prior to the security updates. I even bumped up my DHCP timeout to 3 minutes.

> 
nathacof@nathacof-laptop:~$ lsmod | grep ath
ath5k                 106496  0 
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  1 ath5k
nathacof@nathacof-laptop:~$ grep ^timeout /etc/dhcp3/dhclient.conf 
timeout 360;
nathacof@nathacof-laptop:~$ 


Anyone know how I might go about fixing this issue?

---

