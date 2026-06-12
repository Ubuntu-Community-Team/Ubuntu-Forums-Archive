---
title: "Ubuntu 10.10 bc43 cannot view my created ad-hoc mode"
date: 2010-11-16
forum: Hardware
---

### Post by izlude on 2010-11-16
Hi, i create ad-ho on my notebook. But other devices can't see my AP.

In syslog i have only info records.

[PHP]
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) starting connection 'serj'
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1/wireless): access point 'serj' has security, but secrets are required.
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> (eth1): device state change: 5 -> 6 (reason 0)
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> (eth1): device state change: 6 -> 4 (reason 0)
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1/wireless): connection 'serj' has security, and secrets exist.  No new secrets needed.
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Config: added 'ssid' value 'serj'
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Config: added 'mode' value '1'
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Config: added 'frequency' value '2412'
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Config: added 'key_mgmt' value 'WPA-NONE'
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Config: added 'psk' value '<omitted>'
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Config: added 'proto' value 'WPA'
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Config: added 'pairwise' value 'NONE'
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Config: added 'group' value 'TKIP'
Nov 17 05:43:25 serj-laptop NetworkManager[902]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 17 05:43:25 serj-laptop NetworkManager[902]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Config: set interface ap_scan to 2
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Nov 17 05:43:25 serj-laptop wpa_supplicant[1032]: Trying to associate with SSID 'serj'
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> (eth1): supplicant connection state:  scanning -> associating
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> (eth1): supplicant connection state:  associating -> completed
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'serj'.
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> (eth1): device state change: 5 -> 7 (reason 0)
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) started...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Get) complete.
Nov 17 05:43:25 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
Nov 17 05:43:25 serj-laptop wpa_supplicant[1032]: CTRL-EVENT-CONNECTED - Connection to 00:00:00:00:00:00 completed (reauth) [id=-1 id_str=]
Nov 17 05:43:26 serj-laptop wpa_supplicant[1032]: Associated with 4e:1b:43:d8:6c:7b
Nov 17 05:43:26 serj-laptop wpa_supplicant[1032]: CTRL-EVENT-CONNECTED - Connection to 4e:1b:43:d8:6c:7b completed (reauth) [id=0 id_str=]
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Nov 17 05:43:26 serj-laptop kernel: [125636.676339] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 17 05:43:26 serj-laptop kernel: [125636.710845] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Nov 17 05:43:26 serj-laptop kernel: [125636.711959] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Nov 17 05:43:26 serj-laptop kernel: [125636.711964] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Nov 17 05:43:26 serj-laptop kernel: [125636.711966] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth1 --protocol tcp --destination-port 53 -
-jump ACCEPT
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth1 --protocol udp --destination-port 53 -
-jump ACCEPT
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth1 --protocol tcp --destination-port 67 -
-jump ACCEPT
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth1 --protocol udp --destination-port 67 -
-jump ACCEPT
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth1 --jump REJECT
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --out-interface eth1 --jump REJECT
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth1 --out-interface eth1 --jump ACCEPT
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth1 --
jump ACCEPT
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface e
th1 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42
.43.0/255.255.255.0 --jump MASQUERADE
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Starting dnsmasq...
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> (eth1): device state change: 7 -> 8 (reason 0)
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Activation (eth1) successful, device activated.
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> (eth1): supplicant connection state:  completed -> associated
Nov 17 05:43:26 serj-laptop NetworkManager[902]: <info> (eth1): supplicant connection state:  associated -> completed
Nov 17 05:43:26 serj-laptop dnsmasq[26627]: started, version 2.55 cachesize 150
Nov 17 05:43:26 serj-laptop dnsmasq[26627]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Nov 17 05:43:26 serj-laptop dnsmasq-dhcp[26627]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Nov 17 05:43:26 serj-laptop dnsmasq[26627]: reading /etc/resolv.conf
Nov 17 05:43:26 serj-laptop dnsmasq[26627]: using nameserver 192.168.50.55#53
Nov 17 05:43:26 serj-laptop dnsmasq[26627]: using nameserver 192.168.144.7#53
Nov 17 05:43:26 serj-laptop dnsmasq[26627]: cleared cache
Nov 17 05:43:30 serj-laptop ntpdate[26672]: adjust time server 91.189.94.4 offset 0.010915 sec
Nov 17 05:47:26 serj-laptop AptDaemon: INFO: Quiting due to inactivity
Nov 17 05:47:26 serj-laptop AptDaemon: INFO: Shutdown was requested
Nov 17 05:47:27 serj-laptop AptDaemon: INFO: Initializing daemon

[/PHP]

---

