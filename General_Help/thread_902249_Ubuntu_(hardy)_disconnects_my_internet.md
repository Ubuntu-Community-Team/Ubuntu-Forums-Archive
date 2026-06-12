---
title: "Ubuntu (hardy) disconnects my internet"
date: 2008-08-27
forum: General Help
---

### Post by catabriga on 2008-08-27
I have recently installed ubuntu hardy (amd64) and I'm having this problem with my internet conection, every time I try to download something using synaptic after a few seconds my intert loses its IP, so it have to connect again to get a new IP, after that the download goes for some more seconds and then stops again, with the same problem. This problema ocurred with both wired and wireless connections. Using windows in the same computer, or windows in other computer or even an older version of ubuntu in the laptop won't have any problem. The most strange is that when I was installing hardy in this computer, I had to install it 2 times (because of some problems with windows) and in the first time I installed I could use synaptic with no problem. I use a wireless linksys router.

---

### Post by linux_tech on 2008-08-27
Please post the output of this command...

```
lspci | grep -i wireless
```
this will show wireless card 

Also, after the next disconnect, immediately run this command.

```
cat /var/log/daemon.log > ~/Desktop/daemon.txt
```
This will create a file called daemon.txt on your Desktop. You should run this command again the next time your network drops out; after you re-connect, reply to this thread and attach the file

If the adapter stays connected in windows then it hints toward the driver as being a cause of sporatic connection

```
sudo /etc/init.d/./networking restart
```
to reload wlan

Refer to this re: Ndiswrapper-  This is a Linux module which allows Ubuntu to use the Windows driver for wireless cards
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by catabriga on 2008-08-27
I am already using ndiswrapper to use the internet, and I don't think the problem is related to drivers, because I still had the same problem when I tried to use the internet connected with a wire directly in the router.

I tried to run the lpsci command but it didn't return anything, the log created to the other command is here: 

```
Aug 26 21:13:33 ubuntu-L dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Aug 26 21:13:38 ubuntu-L dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Aug 26 21:13:47 ubuntu-L dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Aug 26 21:13:57 ubuntu-L dhclient: No DHCPOFFERS received.
Aug 26 21:13:57 ubuntu-L avahi-autoipd(wlan0)[6719]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Aug 26 21:13:57 ubuntu-L avahi-autoipd(wlan0)[6719]: Successfully called chroot().
Aug 26 21:13:57 ubuntu-L avahi-autoipd(wlan0)[6719]: Successfully dropped root privileges.
Aug 26 21:13:57 ubuntu-L avahi-autoipd(wlan0)[6719]: Starting with address 169.254.3.82
Aug 26 21:14:02 ubuntu-L avahi-autoipd(wlan0)[6719]: Callout BIND, address 169.254.3.82 on interface wlan0
Aug 26 21:14:02 ubuntu-L avahi-daemon[4968]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.3.82.
Aug 26 21:14:02 ubuntu-L avahi-daemon[4968]: New relevant interface wlan0.IPv4 for mDNS.
Aug 26 21:14:02 ubuntu-L avahi-daemon[4968]: Registering new address record for 169.254.3.82 on wlan0.IPv4.
Aug 26 21:14:06 ubuntu-L avahi-autoipd(wlan0)[6719]: Successfully claimed IP address 169.254.3.82
Aug 26 21:14:06 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 9 (fail) for interface wlan0 
Aug 26 21:14:06 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Aug 26 21:14:06 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Aug 26 21:14:06 ubuntu-L NetworkManager: <debug> [1219796046.337508] real_act_stage4_ip_config_timeout(): Activation (wlan0/wireless): could not get IP configuration info for 'linksys_SES_15106', asking for new key. 
Aug 26 21:14:06 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
Aug 26 21:14:06 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'linksys_SES_15106'. 
Aug 26 21:14:06 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Aug 26 21:14:16 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key request for network 'linksys_SES_15106' was canceled. 
Aug 26 21:14:16 ubuntu-L NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Aug 26 21:14:16 ubuntu-L NetworkManager: <info>  Activation (wlan0) failed for access point (linksys_SES_15106) 
Aug 26 21:14:16 ubuntu-L NetworkManager: <info>  Activation (wlan0) failed. 
Aug 26 21:14:16 ubuntu-L NetworkManager: <info>  Deactivating device wlan0. 
Aug 26 21:14:16 ubuntu-L avahi-daemon[4968]: Withdrawing address record for 169.254.3.82 on wlan0.
Aug 26 21:14:16 ubuntu-L avahi-daemon[4968]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.3.82.
Aug 26 21:14:16 ubuntu-L avahi-daemon[4968]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 26 21:14:16 ubuntu-L avahi-daemon[4968]: Withdrawing address record for fe80::20c:41ff:fe6a:1041 on wlan0.
Aug 26 21:14:16 ubuntu-L NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 26 21:15:03 ubuntu-L NetworkManager: <debug> [1219796103.640868] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'linksys_SES_15106' 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / linksys_SES_15106 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Deactivating device wlan0. 
Aug 26 21:15:03 ubuntu-L NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Device wlan0 activation scheduled... 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Activation (wlan0) started... 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, but NO valid key exists.  New key needed. 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'linksys_SES_15106'. 
Aug 26 21:15:03 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 26 21:15:05 ubuntu-L NetworkManager: <info>  SWITCH: terminating current connection 'wlan0' because it's no longer valid. 
Aug 26 21:15:05 ubuntu-L NetworkManager: <info>  Deactivating device wlan0. 
Aug 26 21:15:05 ubuntu-L NetworkManager: <info>  Activation (wlan0): cancelling... 
Aug 26 21:15:05 ubuntu-L NetworkManager: <info>  Activation (wlan0) cancellation handler scheduled... 
Aug 26 21:15:05 ubuntu-L NetworkManager: <info>  Activation (wlan0): waiting for device to cancel activation. 
Aug 26 21:15:05 ubuntu-L NetworkManager: <info>  Activation (wlan0) cancellation handled. 
Aug 26 21:15:05 ubuntu-L NetworkManager: <info>  Activation (wlan0): cancelled. 
Aug 26 21:15:05 ubuntu-L NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 26 21:15:05 ubuntu-L NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Aug 26 21:15:05 ubuntu-L NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Aug 26 21:15:22 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'linksys_SES_15106' received. 
Aug 26 21:15:22 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 26 21:15:22 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 26 21:15:22 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 26 21:15:22 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 26 21:15:22 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 26 21:15:22 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, and a key exists.  No new key needed. 
Aug 26 21:15:23 ubuntu-L NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Aug 26 21:15:23 ubuntu-L NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Aug 26 21:15:23 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: response was '0' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b7379735f5345535f3135313036' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:24 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 26 21:15:31 ubuntu-L NetworkManager: <debug> [1219796131.199869] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'linksys_SES_15106' 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / linksys_SES_15106 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Deactivating device wlan0. 
Aug 26 21:15:31 ubuntu-L NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Device wlan0 activation scheduled... 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Activation (wlan0) started... 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, but NO valid key exists.  New key needed. 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'linksys_SES_15106'. 
Aug 26 21:15:31 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 26 21:15:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key request for network 'linksys_SES_15106' was canceled. 
Aug 26 21:15:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Aug 26 21:15:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) failed for access point (linksys_SES_15106) 
Aug 26 21:15:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) failed. 
Aug 26 21:15:34 ubuntu-L NetworkManager: <info>  Deactivating device wlan0. 
Aug 26 21:15:35 ubuntu-L NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 26 21:15:38 ubuntu-L NetworkManager: <debug> [1219796138.212753] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'linksys_SES_15106' 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / linksys_SES_15106 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Deactivating device wlan0. 
Aug 26 21:15:38 ubuntu-L NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Device wlan0 activation scheduled... 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Activation (wlan0) started... 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, but NO valid key exists.  New key needed. 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'linksys_SES_15106'. 
Aug 26 21:15:38 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 26 21:15:54 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'linksys_SES_15106' received. 
Aug 26 21:15:54 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 26 21:15:54 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 26 21:15:54 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 26 21:15:54 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 26 21:15:54 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 26 21:15:54 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, and a key exists.  No new key needed. 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: response was '0' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b7379735f5345535f3135313036' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:15:56 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 26 21:15:59 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 26 21:15:59 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'linksys_SES_15106'. 
Aug 26 21:15:59 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 26 21:15:59 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Aug 26 21:16:01 ubuntu-L avahi-daemon[4968]: Registering new address record for fe80::20c:41ff:fe6a:1041 on wlan0.*.
Aug 26 21:16:01 ubuntu-L NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Aug 26 21:16:01 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Aug 26 21:16:01 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Aug 26 21:16:01 ubuntu-L avahi-autoipd(wlan0)[6719]: Got SIGTERM, quitting.
Aug 26 21:16:01 ubuntu-L avahi-autoipd(wlan0)[6719]: Callout STOP, address 169.254.3.82 on interface wlan0
Aug 26 21:16:01 ubuntu-L avahi-autoipd(wlan0)[6720]: client: RTNETLINK answers: Cannot assign requested address
Aug 26 21:16:01 ubuntu-L avahi-autoipd(wlan0)[6720]: Script execution failed with return value 2
Aug 26 21:16:02 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Aug 26 21:16:05 ubuntu-L dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Aug 26 21:16:06 ubuntu-L dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
Aug 26 21:16:06 ubuntu-L dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
Aug 26 21:16:07 ubuntu-L dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Aug 26 21:16:07 ubuntu-L avahi-daemon[4968]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 26 21:16:07 ubuntu-L avahi-daemon[4968]: New relevant interface wlan0.IPv4 for mDNS.
Aug 26 21:16:07 ubuntu-L avahi-daemon[4968]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Aug 26 21:16:07 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
Aug 26 21:16:07 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 26 21:16:07 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Aug 26 21:16:07 ubuntu-L dhclient: bound to 192.168.1.101 -- renewal in 37709 seconds.
Aug 26 21:16:08 ubuntu-L NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Aug 26 21:16:08 ubuntu-L NetworkManager: <info>    address 192.168.1.101 
Aug 26 21:16:08 ubuntu-L NetworkManager: <info>    netmask 255.255.255.0 
Aug 26 21:16:08 ubuntu-L NetworkManager: <info>    broadcast 192.168.1.255 
Aug 26 21:16:08 ubuntu-L NetworkManager: <info>    gateway 192.168.1.1 
Aug 26 21:16:08 ubuntu-L NetworkManager: <info>    nameserver 200.165.132.147 
Aug 26 21:16:08 ubuntu-L NetworkManager: <info>    nameserver 200.149.55.140 
Aug 26 21:16:08 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 26 21:16:08 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Aug 26 21:16:08 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Aug 26 21:16:08 ubuntu-L avahi-daemon[4968]: Withdrawing address record for 192.168.1.101 on wlan0.
Aug 26 21:16:08 ubuntu-L avahi-daemon[4968]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 26 21:16:08 ubuntu-L avahi-daemon[4968]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 26 21:16:08 ubuntu-L avahi-daemon[4968]: Withdrawing address record for fe80::20c:41ff:fe6a:1041 on wlan0.
Aug 26 21:16:08 ubuntu-L avahi-daemon[4968]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 26 21:16:08 ubuntu-L avahi-daemon[4968]: New relevant interface wlan0.IPv4 for mDNS.
Aug 26 21:16:08 ubuntu-L avahi-daemon[4968]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Aug 26 21:16:09 ubuntu-L NetworkManager: <info>  Clearing nscd hosts cache. 
Aug 26 21:16:09 ubuntu-L NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Aug 26 21:16:09 ubuntu-L NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Aug 26 21:16:09 ubuntu-L NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Aug 26 21:16:09 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 26 21:16:09 ubuntu-L NetworkManager: <debug> [1219796169.258338] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'linksys_SES_15106' 
Aug 26 21:16:09 ubuntu-L NetworkManager: <debug> [1219796169.258575] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'linksys_SES_15106' 
Aug 26 21:16:09 ubuntu-L NetworkManager: <debug> [1219796169.258720] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'linksys_SES_15106' 
Aug 26 21:16:09 ubuntu-L NetworkManager: <debug> [1219796169.258863] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'linksys_SES_15106' 
Aug 26 21:16:09 ubuntu-L NetworkManager: <debug> [1219796169.259008] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'linksys_SES_15106' 
Aug 26 21:16:09 ubuntu-L NetworkManager: <info>  SWITCH: terminating current connection 'wlan0' because it's no longer valid. 
Aug 26 21:16:09 ubuntu-L NetworkManager: <info>  Deactivating device wlan0. 
Aug 26 21:16:09 ubuntu-L dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 6844
Aug 26 21:16:09 ubuntu-L dhclient: killed old client process, removed PID file
Aug 26 21:16:09 ubuntu-L dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Aug 26 21:16:09 ubuntu-L avahi-daemon[4968]: Withdrawing address record for 192.168.1.101 on wlan0.
Aug 26 21:16:09 ubuntu-L avahi-daemon[4968]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 26 21:16:09 ubuntu-L avahi-daemon[4968]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 26 21:16:09 ubuntu-L ntpdate[6915]: can't find host ntp.ubuntu.com 
Aug 26 21:16:09 ubuntu-L ntpdate[6915]: no servers can be used, exiting
Aug 26 21:16:10 ubuntu-L NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 26 21:16:10 ubuntu-L NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Aug 26 21:16:10 ubuntu-L NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Aug 26 21:16:26 ubuntu-L NetworkManager: <debug> [1219796186.130158] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'linksys_SES_15106' 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / linksys_SES_15106 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Deactivating device wlan0. 
Aug 26 21:16:26 ubuntu-L NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Device wlan0 activation scheduled... 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) started... 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, but NO valid key exists.  New key needed. 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'linksys_SES_15106'. 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'linksys_SES_15106' received. 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 26 21:16:26 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, and a key exists.  No new key needed. 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: response was '0' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b7379735f5345535f3135313036' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 26 21:16:27 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 26 21:16:31 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 26 21:16:31 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'linksys_SES_15106'. 
Aug 26 21:16:31 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 26 21:16:31 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Aug 26 21:16:32 ubuntu-L NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Aug 26 21:16:32 ubuntu-L dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Aug 26 21:16:32 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Aug 26 21:16:32 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Aug 26 21:16:32 ubuntu-L avahi-daemon[4968]: Registering new address record for fe80::20c:41ff:fe6a:1041 on wlan0.*.
Aug 26 21:16:33 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Aug 26 21:16:37 ubuntu-L dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 26 21:16:38 ubuntu-L dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
Aug 26 21:16:38 ubuntu-L dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
Aug 26 21:16:39 ubuntu-L dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Aug 26 21:16:39 ubuntu-L avahi-daemon[4968]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 26 21:16:39 ubuntu-L avahi-daemon[4968]: New relevant interface wlan0.IPv4 for mDNS.
Aug 26 21:16:39 ubuntu-L avahi-daemon[4968]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Aug 26 21:16:39 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
Aug 26 21:16:39 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 26 21:16:39 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Aug 26 21:16:39 ubuntu-L dhclient: bound to 192.168.1.101 -- renewal in 38444 seconds.
Aug 26 21:16:40 ubuntu-L NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Aug 26 21:16:40 ubuntu-L NetworkManager: <info>    address 192.168.1.101 
Aug 26 21:16:40 ubuntu-L NetworkManager: <info>    netmask 255.255.255.0 
Aug 26 21:16:40 ubuntu-L NetworkManager: <info>    broadcast 192.168.1.255 
Aug 26 21:16:40 ubuntu-L NetworkManager: <info>    gateway 192.168.1.1 
Aug 26 21:16:40 ubuntu-L NetworkManager: <info>    nameserver 200.165.132.147 
Aug 26 21:16:40 ubuntu-L NetworkManager: <info>    nameserver 200.149.55.140 
Aug 26 21:16:40 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 26 21:16:40 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Aug 26 21:16:40 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Aug 26 21:16:40 ubuntu-L avahi-daemon[4968]: Withdrawing address record for 192.168.1.101 on wlan0.
Aug 26 21:16:40 ubuntu-L avahi-daemon[4968]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 26 21:16:40 ubuntu-L avahi-daemon[4968]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 26 21:16:40 ubuntu-L avahi-daemon[4968]: Withdrawing address record for fe80::20c:41ff:fe6a:1041 on wlan0.
Aug 26 21:16:40 ubuntu-L avahi-daemon[4968]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 26 21:16:40 ubuntu-L avahi-daemon[4968]: New relevant interface wlan0.IPv4 for mDNS.
Aug 26 21:16:40 ubuntu-L avahi-daemon[4968]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Aug 26 21:16:41 ubuntu-L NetworkManager: <info>  Clearing nscd hosts cache. 
Aug 26 21:16:41 ubuntu-L NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Aug 26 21:16:41 ubuntu-L NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Aug 26 21:16:41 ubuntu-L NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Aug 26 21:16:41 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 26 21:16:41 ubuntu-L NetworkManager: <debug> [1219796201.187006] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'linksys_SES_15106' 
Aug 26 22:16:42 ubuntu-L ntpdate[7044]: step time server 91.189.94.4 offset 3599.678610 sec
Aug 26 22:16:42 ubuntu-L avahi-daemon[4968]: Registering new address record for fe80::20c:41ff:fe6a:1041 on wlan0.*.
Aug 26 23:47:20 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 01:18:56 ubuntu-L NetworkManager: <info>  Supplicant state changed: 0 
Aug 27 01:18:59 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 02:54:39 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 03:05:30 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 03:29:21 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 03:33:42 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 03:53:14 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 04:30:05 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 04:53:56 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 05:02:37 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 05:06:58 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 05:41:40 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 06:05:31 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 06:17:33 ubuntu-L NetworkManager: <debug> [1219828653.607822] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_ROM_TS_H352C'). 
Aug 27 07:17:40 ubuntu-L init: tty4 main process (4526) killed by TERM signal
Aug 27 07:17:40 ubuntu-L init: tty5 main process (4527) killed by TERM signal
Aug 27 07:17:40 ubuntu-L init: tty2 main process (4529) killed by TERM signal
Aug 27 07:17:40 ubuntu-L init: tty3 main process (4532) killed by TERM signal
Aug 27 07:17:40 ubuntu-L init: tty1 main process (5452) killed by TERM signal
Aug 27 07:17:40 ubuntu-L init: tty6 main process (4533) killed by TERM signal
Aug 27 07:17:41 ubuntu-L gdm[5296]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Aug 27 07:17:41 ubuntu-L gdm[5296]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Aug 27 07:18:10 ubuntu-L avahi-daemon[4968]: Got SIGTERM, quitting.
Aug 27 07:18:10 ubuntu-L avahi-daemon[4968]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 27 07:19:03 ubuntu-L NetworkManager: <info>  starting... 
Aug 27 07:19:03 ubuntu-L avahi-daemon[5020]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 27 07:19:03 ubuntu-L avahi-daemon[5020]: Successfully dropped root privileges.
Aug 27 07:19:03 ubuntu-L avahi-daemon[5020]: avahi-daemon 0.6.22 starting up.
Aug 27 07:19:03 ubuntu-L avahi-daemon[5020]: Successfully called chroot().
Aug 27 07:19:03 ubuntu-L avahi-daemon[5020]: Successfully dropped remaining capabilities.
Aug 27 07:19:03 ubuntu-L avahi-daemon[5020]: No service file found in /etc/avahi/services.
Aug 27 07:19:03 ubuntu-L avahi-daemon[5020]: Network interface enumeration completed.
Aug 27 07:19:03 ubuntu-L avahi-daemon[5020]: Registering HINFO record with values 'X86_64'/'LINUX'.
Aug 27 07:19:03 ubuntu-L avahi-daemon[5020]: Server startup complete. Host name is ubuntu-L.local. Local service cookie is 562011409.
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'. 
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  Deactivating device eth0. 
Aug 27 07:19:04 ubuntu-L hcid[5273]: Bluetooth HCI daemon
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  Deactivating device wlan0. 
Aug 27 07:19:04 ubuntu-L NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 27 07:19:04 ubuntu-L NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Aug 27 07:19:04 ubuntu-L NetworkManager: <debug> [1219832344.858749] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_ROM_TS_H352C'). 
Aug 27 07:19:04 ubuntu-L hcid[5273]: Starting SDP server
Aug 27 07:19:04 ubuntu-L hcid[5273]: Created local server at unix:abstract=/var/run/dbus-vw9PVISlC3,guid=05f12312d0c41ddf2e612b8348b52a18
Aug 27 07:19:04 ubuntu-L NetworkManager: <debug> [1219832344.943785] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 27 07:19:04 ubuntu-L audio[5329]: Bluetooth Audio daemon
Aug 27 07:19:04 ubuntu-L audio[5329]: Unix socket created: 5
Aug 27 07:19:04 ubuntu-L audio[5329]: audio.conf: Key file does not have key 'Enable'
Aug 27 07:19:04 ubuntu-L audio[5329]: audio.conf: Key file does not have key 'Disable'
Aug 27 07:19:04 ubuntu-L audio[5329]: add_service_record: got record id 0x10000
Aug 27 07:19:04 ubuntu-L audio[5329]: audio.conf: Key file does not have key 'Disable'
Aug 27 07:19:04 ubuntu-L audio[5329]: audio.conf: Key file does not have group 'A2DP'
Aug 27 07:19:04 ubuntu-L last message repeated 3 times
Aug 27 07:19:04 ubuntu-L audio[5329]: SEP 0x62d450 registered: type:0 codec:0 seid:1
Aug 27 07:19:04 ubuntu-L input[5341]: Bluetooth Input daemon
Aug 27 07:19:04 ubuntu-L audio[5329]: add_service_record: got record id 0x10001
Aug 27 07:19:04 ubuntu-L audio[5329]: add_service_record: got record id 0x10002
Aug 27 07:19:04 ubuntu-L input[5341]: Registered input manager path:/org/bluez/input
Aug 27 07:19:04 ubuntu-L audio[5329]: add_service_record: got record id 0x10003
Aug 27 07:19:04 ubuntu-L audio[5329]: Registered manager path:/org/bluez/audio
Aug 27 07:19:06 ubuntu-L NetworkManager: <debug> [1219832346.952706] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_5954_drm_r300_card0'). 
Aug 27 07:19:24 ubuntu-L gdm[5374]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Aug 27 07:19:24 ubuntu-L gdm[5374]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
Aug 27 07:19:24 ubuntu-L gdm[5571]: Gtk-WARNING: Ignoring the separator setting 
Aug 27 07:19:30 ubuntu-L hcid[5273]: Default passkey agent (:1.23, /org/bluez/passkey) registered
Aug 27 07:19:30 ubuntu-L hcid[5273]: Default authorization agent (:1.23, /org/bluez/auth) registered
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Will activate connection 'wlan0/linksys_SES_15106'. 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Device wlan0 activation scheduled... 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) started... 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, but NO valid key exists.  New key needed. 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'linksys_SES_15106'. 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'linksys_SES_15106' received. 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 27 07:19:34 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, and a key exists.  No new key needed. 
Aug 27 07:19:35 ubuntu-L NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: response was '0' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b7379735f5345535f3135313036' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 07:19:36 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 27 07:19:39 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 07:19:39 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'linksys_SES_15106'. 
Aug 27 07:19:39 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 27 07:19:39 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Aug 27 07:19:40 ubuntu-L NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Aug 27 07:19:40 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Aug 27 07:19:40 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Aug 27 07:19:40 ubuntu-L avahi-daemon[5020]: Registering new address record for fe80::20c:41ff:fe6a:1041 on wlan0.*.
Aug 27 07:19:41 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Aug 27 07:19:45 ubuntu-L dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
Aug 27 07:19:45 ubuntu-L dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Aug 27 07:19:45 ubuntu-L dhclient: bound to 192.168.1.101 -- renewal in 37652 seconds.
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface wlan0 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>    address 192.168.1.101 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>    netmask 255.255.255.0 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>    broadcast 192.168.1.255 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>    gateway 192.168.1.1 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>    nameserver 200.165.132.147 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>    nameserver 200.149.55.140 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Aug 27 07:19:45 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: Withdrawing address record for 192.168.1.101 on wlan0.
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: Withdrawing address record for fe80::20c:41ff:fe6a:1041 on wlan0.
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Aug 27 07:19:46 ubuntu-L NetworkManager: <info>  Clearing nscd hosts cache. 
Aug 27 07:19:46 ubuntu-L NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Aug 27 07:19:46 ubuntu-L NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Aug 27 07:19:46 ubuntu-L NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Aug 27 07:19:46 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 27 07:19:45 ubuntu-L ntpdate[5775]: step time server 91.189.94.4 offset -2.302034 sec
Aug 27 07:19:45 ubuntu-L avahi-daemon[5020]: Registering new address record for fe80::20c:41ff:fe6a:1041 on wlan0.*.
Aug 27 07:22:03 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 07:23:49 ubuntu-L NetworkManager: <info>  Supplicant state changed: 0 
Aug 27 07:23:52 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 07:45:23 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 07:51:15 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 08:07:36 ubuntu-L NetworkManager: <info>  Supplicant state changed: 0 
Aug 27 08:07:40 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 08:54:47 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 09:41:24 ubuntu-L atieventsd[6396]: ATI External Events Daemon started... 
Aug 27 09:41:24 ubuntu-L atieventsd[6396]: Event daemon control socket created 
Aug 27 09:41:24 ubuntu-L atieventsd[6396]: acpid connection established 
Aug 27 10:32:45 ubuntu-L NetworkManager: <info>  Supplicant state changed: 0 
Aug 27 10:32:48 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 11:33:26 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 11:44:17 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 11:59:28 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 12:06:00 ubuntu-L NetworkManager: <info>  Supplicant state changed: 0 
Aug 27 12:06:03 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 12:10:21 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 12:37:49 ubuntu-L init: tty4 main process (4578) killed by TERM signal
Aug 27 12:37:49 ubuntu-L init: tty5 main process (4579) killed by TERM signal
Aug 27 12:37:49 ubuntu-L init: tty2 main process (4583) killed by TERM signal
Aug 27 12:37:49 ubuntu-L init: tty3 main process (4584) killed by TERM signal
Aug 27 12:37:49 ubuntu-L init: tty6 main process (4585) killed by TERM signal
Aug 27 12:37:49 ubuntu-L init: tty1 main process (5527) killed by TERM signal
Aug 27 12:37:50 ubuntu-L gdm[5371]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Aug 27 12:37:50 ubuntu-L gdm[5371]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Aug 27 12:37:50 ubuntu-L avahi-daemon[5020]: Got SIGTERM, quitting.
Aug 27 12:37:50 ubuntu-L avahi-daemon[5020]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 27 14:37:11 ubuntu-L NetworkManager: <info>  starting... 
Aug 27 14:37:11 ubuntu-L avahi-daemon[5024]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 27 14:37:11 ubuntu-L avahi-daemon[5024]: Successfully dropped root privileges.
Aug 27 14:37:11 ubuntu-L avahi-daemon[5024]: avahi-daemon 0.6.22 starting up.
Aug 27 14:37:11 ubuntu-L avahi-daemon[5024]: Successfully called chroot().
Aug 27 14:37:11 ubuntu-L avahi-daemon[5024]: Successfully dropped remaining capabilities.
Aug 27 14:37:11 ubuntu-L avahi-daemon[5024]: No service file found in /etc/avahi/services.
Aug 27 14:37:11 ubuntu-L avahi-daemon[5024]: Network interface enumeration completed.
Aug 27 14:37:11 ubuntu-L avahi-daemon[5024]: Registering HINFO record with values 'X86_64'/'LINUX'.
Aug 27 14:37:11 ubuntu-L avahi-daemon[5024]: Server startup complete. Host name is ubuntu-L.local. Local service cookie is 2859855190.
Aug 27 14:37:11 ubuntu-L atieventsd[5044]: ATI External Events Daemon started... 
Aug 27 14:37:11 ubuntu-L atieventsd[5044]: Event daemon control socket created 
Aug 27 14:37:11 ubuntu-L atieventsd[5044]: acpid connection established 
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'. 
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  Deactivating device eth0. 
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  wlan0: Device is fully-supported using driver 'ndiswrapper'. 
Aug 27 14:37:12 ubuntu-L hcid[5295]: Bluetooth HCI daemon
Aug 27 14:37:12 ubuntu-L hcid[5295]: Starting SDP server
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  Deactivating device wlan0. 
Aug 27 14:37:12 ubuntu-L NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 27 14:37:12 ubuntu-L hcid[5295]: Created local server at unix:abstract=/var/run/dbus-MmerYIQoOd,guid=b6bb1a693107f89916489add48b590c8
Aug 27 14:37:12 ubuntu-L NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Aug 27 14:37:12 ubuntu-L NetworkManager: <debug> [1219858632.904949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_ROM_TS_H352C'). 
Aug 27 14:37:12 ubuntu-L audio[5316]: Bluetooth Audio daemon
Aug 27 14:37:12 ubuntu-L audio[5316]: Unix socket created: 5
Aug 27 14:37:12 ubuntu-L audio[5316]: audio.conf: Key file does not have key 'Enable'
Aug 27 14:37:12 ubuntu-L audio[5316]: audio.conf: Key file does not have key 'Disable'
Aug 27 14:37:12 ubuntu-L NetworkManager: <debug> [1219858632.948606] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Aug 27 14:37:12 ubuntu-L input[5340]: Bluetooth Input daemon
Aug 27 14:37:12 ubuntu-L input[5340]: Registered input manager path:/org/bluez/input
Aug 27 14:37:12 ubuntu-L audio[5316]: add_service_record: got record id 0x10000
Aug 27 14:37:12 ubuntu-L audio[5316]: audio.conf: Key file does not have key 'Disable'
Aug 27 14:37:12 ubuntu-L audio[5316]: audio.conf: Key file does not have group 'A2DP'
Aug 27 14:37:12 ubuntu-L last message repeated 3 times
Aug 27 14:37:12 ubuntu-L audio[5316]: SEP 0x62d450 registered: type:0 codec:0 seid:1
Aug 27 14:37:12 ubuntu-L audio[5316]: add_service_record: got record id 0x10001
Aug 27 14:37:12 ubuntu-L audio[5316]: add_service_record: got record id 0x10002
Aug 27 14:37:12 ubuntu-L audio[5316]: add_service_record: got record id 0x10003
Aug 27 14:37:12 ubuntu-L audio[5316]: Registered manager path:/org/bluez/audio
Aug 27 14:37:36 ubuntu-L hcid[5295]: Default passkey agent (:1.25, /org/bluez/passkey) registered
Aug 27 14:37:36 ubuntu-L hcid[5295]: Default authorization agent (:1.25, /org/bluez/auth) registered
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Will activate connection 'wlan0/linksys_SES_15106'. 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Device wlan0 activation scheduled... 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) started... 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, but NO valid key exists.  New key needed. 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'linksys_SES_15106'. 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'linksys_SES_15106' received. 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 27 14:37:42 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless): access point 'linksys_SES_15106' is encrypted, and a key exists.  No new key needed. 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: response was '0' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6c696e6b7379735f5345535f3135313036' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  SUP: response was 'OK' 
Aug 27 14:37:44 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug 27 14:37:48 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
Aug 27 14:37:48 ubuntu-L NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'linksys_SES_15106'. 

Aug 27 14:37:48 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 27 14:37:48 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Aug 27 14:37:49 ubuntu-L NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Aug 27 14:37:49 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Aug 27 14:37:49 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Aug 27 14:37:50 ubuntu-L avahi-daemon[5024]: Registering new address record for fe80::20c:41ff:fe6a:1041 on wlan0.*.
Aug 27 14:37:50 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Aug 27 14:37:53 ubuntu-L dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
Aug 27 14:37:53 ubuntu-L dhclient: DHCPNAK from 192.168.1.1
Aug 27 14:37:53 ubuntu-L avahi-autoipd(wlan0)[5863]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Aug 27 14:37:53 ubuntu-L avahi-autoipd(wlan0)[5863]: Successfully called chroot().
Aug 27 14:37:53 ubuntu-L avahi-autoipd(wlan0)[5863]: Successfully dropped root privileges.
Aug 27 14:37:53 ubuntu-L avahi-autoipd(wlan0)[5863]: Starting with address 169.254.3.82
Aug 27 14:37:57 ubuntu-L avahi-autoipd(wlan0)[5863]: Callout BIND, address 169.254.3.82 on interface wlan0
Aug 27 14:37:57 ubuntu-L avahi-daemon[5024]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.3.82.
Aug 27 14:37:57 ubuntu-L avahi-daemon[5024]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 14:37:57 ubuntu-L avahi-daemon[5024]: Registering new address record for 169.254.3.82 on wlan0.IPv4.
Aug 27 14:38:01 ubuntu-L avahi-autoipd(wlan0)[5863]: Successfully claimed IP address 169.254.3.82
Aug 27 14:38:01 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 10 (unknown) for interface wlan0 
Aug 27 14:38:01 ubuntu-L avahi-autoipd(wlan0)[5863]: Got SIGTERM, quitting.
Aug 27 14:38:01 ubuntu-L avahi-autoipd(wlan0)[5863]: Callout STOP, address 169.254.3.82 on interface wlan0
Aug 27 14:38:01 ubuntu-L avahi-daemon[5024]: Withdrawing address record for 169.254.3.82 on wlan0.
Aug 27 14:38:01 ubuntu-L avahi-daemon[5024]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.3.82.
Aug 27 14:38:01 ubuntu-L avahi-daemon[5024]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 27 14:38:01 ubuntu-L avahi-autoipd(wlan0)[5864]: client: RTNETLINK answers: No such process
Aug 27 14:38:02 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Aug 27 14:38:02 ubuntu-L dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 27 14:38:04 ubuntu-L dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
Aug 27 14:38:04 ubuntu-L dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
Aug 27 14:38:05 ubuntu-L dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Aug 27 14:38:05 ubuntu-L avahi-daemon[5024]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 27 14:38:05 ubuntu-L avahi-daemon[5024]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 14:38:05 ubuntu-L avahi-daemon[5024]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Aug 27 14:38:05 ubuntu-L dhclient: bound to 192.168.1.101 -- renewal in 37071 seconds.
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>    address 192.168.1.101 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>    netmask 255.255.255.0 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>    broadcast 192.168.1.255 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>    gateway 192.168.1.1 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>    nameserver 200.165.132.147 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>    nameserver 200.149.55.140 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Aug 27 14:38:05 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Aug 27 14:38:05 ubuntu-L avahi-daemon[5024]: Withdrawing address record for 192.168.1.101 on wlan0.
Aug 27 14:38:05 ubuntu-L avahi-daemon[5024]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 27 14:38:05 ubuntu-L avahi-daemon[5024]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 27 14:38:05 ubuntu-L avahi-daemon[5024]: Withdrawing address record for fe80::20c:41ff:fe6a:1041 on wlan0.
Aug 27 14:38:05 ubuntu-L avahi-daemon[5024]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Aug 27 14:38:05 ubuntu-L avahi-daemon[5024]: New relevant interface wlan0.IPv4 for mDNS.
Aug 27 14:38:05 ubuntu-L avahi-daemon[5024]: Registering new address record for 192.168.1.101 on wlan0.IPv4.
Aug 27 14:38:06 ubuntu-L NetworkManager: <info>  Clearing nscd hosts cache. 
Aug 27 14:38:06 ubuntu-L NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Aug 27 14:38:06 ubuntu-L NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Aug 27 14:38:06 ubuntu-L NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Aug 27 14:38:06 ubuntu-L NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 27 14:38:07 ubuntu-L avahi-daemon[5024]: Registering new address record for fe80::20c:41ff:fe6a:1041 on wlan0.*.
Aug 27 14:38:07 ubuntu-L ntpdate[5947]: step time server 91.189.94.4 offset -0.634633 sec
Aug 27 14:42:01 ubuntu-L NetworkManager: <info>  Supplicant state changed: 0 
Aug 27 14:42:04 ubuntu-L NetworkManager: <info>  Supplicant state changed: 1 
```

---

### Post by linux_tech on 2008-08-28
If the connection drops do you need to reboot to get it reconnected?
How many times do have to try reconnecting before it stays connected?

Please post results-
dmesg output:```
dmesg 
```
What is your ethernet adapter?
```
lspci |grep Ethernet
```
Please post results-
```
sudo iwlist wlan0 scan
```
Try this to see if this helps connection
```
sudo dhclient
```

You may wish to give Knetworkmanager a try (handles connection better, more control over daemon)
[http://en.opensuse.org/Projects/KNetworkManager#What_is_KNetworkManager.3F](http://en.opensuse.org/Projects/KNetworkManager#What_is_KNetworkManager.3F)
```
sudo apt-get install knetworkmanager
```
or wicd-
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Have you tried running it with no encryption? 
I see some issues w/scanning and setting ssid-
wlan0: driver does not support SSID scans (scan_capa 0x00).
<WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID  
 wpa_supplicant may have issues  (wpa_supplicant initiates scanning and AP selection)

HowTo: WPA with wpa_supplicant
[http://ubuntuforums.org/showthread.php?t=263136&page=11](http://ubuntuforums.org/showthread.php?t=263136&page=11)


Is SSID broadcasting turned off on your router? 
Please post output of ```
cat /etc/wpa_supplicant.conf
```
looking to see setting for ap_scan=2 (correct)
--broadcast toggle-1=on; 2=off)

---

### Post by Crafty Kisses on 2008-08-28
Post these rusults, sorry for all the outputs:
```
dmesg | grep iw
```
Then this one:
```
lshw -C network
```

---

### Post by catabriga on 2008-08-28
I'll try these commands later on today, now I have to go to college...

Anyway, I have tested connectin internet directly in the modem, behind no routers, and the problem disapeared. So I guess my problem is related to the router, I use a linksys wireless router.

One more thing, that I don't know if it's clear, the internet only disconects while I'm downloading, I can browse web pages for hours with no problem, but I cant finish download a file of small as 1 MB without disconnect the internet, but I can connect it back right away. I'll post the commands later, but thanks for the replies.

---

### Post by catabriga on 2008-08-28
> **Codename said:**
> 
```
dmesg | grep iw
```


I got no results for this.


> **Codename said:**
> 
```
lshw -C network
```

This one returned this:

```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:50:99:1d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:6a:10:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wusb54gv4-x64 driverversion=1.52+Ralink Technology, Inc.,07/ ip=192.168.1.101 link=yes multicast=yes wireless=IEEE 802.11g

```

---

