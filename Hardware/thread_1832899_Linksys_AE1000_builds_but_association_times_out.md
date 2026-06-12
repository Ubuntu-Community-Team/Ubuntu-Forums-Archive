---
title: "Linksys AE1000 builds but association times out"
date: 2011-08-25
forum: Hardware
---

### Post by kai4785 on 2011-08-25
I'm pretty familiar with the AE1000 USB device, and it works on my machine in Windows and Fedora, but I can't seem to get it working in Ubuntu. There are lots of tutorials online (even a youtube video) on how to build the driver. I've tried 3 or 4 of them, and I always get to the same spot. I can't say for sure it's a problem with the network driver, but I'm stumped. Here's syslog from my attempt to associate with my AP:

```
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) starting connection 'Auto Kai'
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> (ra0): device state change: 3 -> 4 (reason 0)
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> (ra0): device state change: 4 -> 5 (reason 0)
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0/wireless): access point 'Auto Kai' has security, but secrets are required.
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> (ra0): device state change: 5 -> 6 (reason 0)
Aug 25 10:21:16 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> (ra0): device state change: 6 -> 4 (reason 0)
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> (ra0): device state change: 4 -> 5 (reason 0)
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0/wireless): connection 'Auto Kai' has security, and secrets exist.  No new secrets needed.
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Config: added 'ssid' value 'Kai'
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Config: added 'scan_ssid' value '1'
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Config: added 'psk' value '<omitted>'
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> Config: set interface ap_scan to 1
Aug 25 10:21:35 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 25 10:21:38 gamer-ubuntu wpa_supplicant[1100]: Trying to associate with c0:c1:c0:77:3d:5c (SSID='Kai' freq=2437 MHz)
Aug 25 10:21:38 gamer-ubuntu wpa_supplicant[1100]: Association request to the driver failed
Aug 25 10:21:38 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 25 10:21:38 gamer-ubuntu kernel: [49514.973089] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:21:38 gamer-ubuntu kernel: [49514.973360] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Aug 25 10:21:38 gamer-ubuntu kernel: [49514.991026] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:21:43 gamer-ubuntu wpa_supplicant[1100]: Authentication with c0:c1:c0:77:3d:5c timed out.
Aug 25 10:21:43 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  associating -> disconnected
Aug 25 10:21:43 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 25 10:21:46 gamer-ubuntu wpa_supplicant[1100]: Trying to associate with c0:c1:c0:77:3d:5c (SSID='Kai' freq=2437 MHz)
Aug 25 10:21:46 gamer-ubuntu wpa_supplicant[1100]: Association request to the driver failed
Aug 25 10:21:46 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 25 10:21:46 gamer-ubuntu kernel: [49522.876585] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:21:46 gamer-ubuntu kernel: [49522.876807] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Aug 25 10:21:46 gamer-ubuntu kernel: [49522.879056] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:21:51 gamer-ubuntu wpa_supplicant[1100]: Authentication with c0:c1:c0:77:3d:5c timed out.
Aug 25 10:21:51 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  associating -> disconnected
Aug 25 10:21:51 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 25 10:21:54 gamer-ubuntu wpa_supplicant[1100]: Trying to associate with c0:c1:c0:77:3d:5c (SSID='Kai' freq=2437 MHz)
Aug 25 10:21:54 gamer-ubuntu wpa_supplicant[1100]: Association request to the driver failed
Aug 25 10:21:54 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 25 10:21:54 gamer-ubuntu kernel: [49530.783235] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:21:54 gamer-ubuntu kernel: [49530.783475] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Aug 25 10:21:54 gamer-ubuntu kernel: [49530.795830] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:21:59 gamer-ubuntu wpa_supplicant[1100]: Authentication with c0:c1:c0:77:3d:5c timed out.
Aug 25 10:21:59 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  associating -> disconnected
Aug 25 10:21:59 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 25 10:22:02 gamer-ubuntu wpa_supplicant[1100]: Trying to associate with c0:c1:c0:77:3d:5c (SSID='Kai' freq=2437 MHz)
Aug 25 10:22:02 gamer-ubuntu wpa_supplicant[1100]: Association request to the driver failed
Aug 25 10:22:02 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 25 10:22:02 gamer-ubuntu kernel: [49538.684509] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1444
Aug 25 10:22:02 gamer-ubuntu kernel: [49538.684824] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Aug 25 10:22:02 gamer-ubuntu kernel: [49538.688841] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1444
Aug 25 10:22:07 gamer-ubuntu wpa_supplicant[1100]: Authentication with c0:c1:c0:77:3d:5c timed out.
Aug 25 10:22:07 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  associating -> disconnected
Aug 25 10:22:07 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 25 10:22:10 gamer-ubuntu wpa_supplicant[1100]: Trying to associate with c0:c1:c0:77:3d:5c (SSID='Kai' freq=2437 MHz)
Aug 25 10:22:10 gamer-ubuntu wpa_supplicant[1100]: Association request to the driver failed
Aug 25 10:22:10 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 25 10:22:10 gamer-ubuntu kernel: [49546.603608] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:22:10 gamer-ubuntu kernel: [49546.603899] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Aug 25 10:22:10 gamer-ubuntu kernel: [49546.615470] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:22:13 gamer-ubuntu NetworkManager[821]: <warn> (ra0): link timed out.
Aug 25 10:22:15 gamer-ubuntu wpa_supplicant[1100]: Authentication with c0:c1:c0:77:3d:5c timed out.
Aug 25 10:22:15 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  associating -> disconnected
Aug 25 10:22:15 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 25 10:22:17 gamer-ubuntu wpa_supplicant[1100]: Trying to associate with c0:c1:c0:77:3d:5c (SSID='Kai' freq=2437 MHz)
Aug 25 10:22:17 gamer-ubuntu wpa_supplicant[1100]: Association request to the driver failed
Aug 25 10:22:17 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 25 10:22:17 gamer-ubuntu kernel: [49554.504472] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:22:17 gamer-ubuntu kernel: [49554.504706] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Aug 25 10:22:17 gamer-ubuntu kernel: [49554.506758] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:22:22 gamer-ubuntu wpa_supplicant[1100]: Authentication with c0:c1:c0:77:3d:5c timed out.
Aug 25 10:22:22 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  associating -> disconnected
Aug 25 10:22:22 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 25 10:22:25 gamer-ubuntu wpa_supplicant[1100]: Trying to associate with c0:c1:c0:77:3d:5c (SSID='Kai' freq=2437 MHz)
Aug 25 10:22:25 gamer-ubuntu wpa_supplicant[1100]: Association request to the driver failed
Aug 25 10:22:25 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 25 10:22:25 gamer-ubuntu kernel: [49562.403623] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:22:25 gamer-ubuntu kernel: [49562.403906] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Aug 25 10:22:25 gamer-ubuntu kernel: [49562.406007] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:22:30 gamer-ubuntu wpa_supplicant[1100]: Authentication with c0:c1:c0:77:3d:5c timed out.
Aug 25 10:22:30 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  associating -> disconnected
Aug 25 10:22:30 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 25 10:22:33 gamer-ubuntu wpa_supplicant[1100]: Trying to associate with c0:c1:c0:77:3d:5c (SSID='Kai' freq=2437 MHz)
Aug 25 10:22:33 gamer-ubuntu wpa_supplicant[1100]: Association request to the driver failed
Aug 25 10:22:33 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 25 10:22:33 gamer-ubuntu kernel: [49570.323601] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:22:33 gamer-ubuntu kernel: [49570.323875] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Aug 25 10:22:33 gamer-ubuntu kernel: [49570.326430] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1379
Aug 25 10:22:35 gamer-ubuntu NetworkManager[821]: <warn> Activation (ra0/wireless): association took too long.
Aug 25 10:22:35 gamer-ubuntu NetworkManager[821]: <info> (ra0): device state change: 5 -> 6 (reason 0)
Aug 25 10:22:35 gamer-ubuntu NetworkManager[821]: <warn> Activation (ra0/wireless): asking for new secrets
Aug 25 10:22:35 gamer-ubuntu NetworkManager[821]: <info> (ra0): supplicant connection state:  associating -> disconnected

```

Any ideas?

---

### Post by kai4785 on 2011-08-25
Ok, so I tried a second Access Point, and was able to connect. Grr... Both APs are Linksys routers too. The one that I can't connect to is a Linksys E2000. The one that is working is also a Linksys, but it's older and I don't remember which one it is.

Here is syslog from the successful connection to the older Linksys AP.
```
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) starting connection 'Auto Philly'
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> (ra0): device state change: 3 -> 4 (reason 0)
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> (ra0): device state change: 4 -> 5 (reason 0)
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0/wireless): access point 'Auto Philly' has security, but secrets are required.
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> (ra0): device state change: 5 -> 6 (reason 0)
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> (ra0): device state change: 6 -> 4 (reason 0)
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> (ra0): device state change: 4 -> 5 (reason 0)
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0/wireless): connection 'Auto Philly' has security, and secrets exist.  No new secrets needed.
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Config: added 'ssid' value 'Philly'
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Config: added 'scan_ssid' value '1'
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Config: added 'psk' value '<omitted>'
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> Config: set interface ap_scan to 1
Aug 25 10:48:18 gamer-ubuntu NetworkManager[709]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 25 10:48:48 gamer-ubuntu wpa_supplicant[1112]: Trying to associate with 00:25:9c:5e:82:3d (SSID='Philly' freq=2412 MHz)
Aug 25 10:48:48 gamer-ubuntu NetworkManager[709]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 25 10:48:48 gamer-ubuntu kernel: [  230.531709] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1419
Aug 25 10:48:48 gamer-ubuntu kernel: [  230.531925] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Aug 25 10:48:49 gamer-ubuntu wpa_supplicant[1112]: Associated with 00:25:9c:5e:82:3d
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> (ra0): supplicant connection state:  associating -> associated
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> (ra0): supplicant connection state:  associated -> 4-way handshake
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> (ra0): supplicant connection state:  4-way handshake -> group handshake
Aug 25 10:48:49 gamer-ubuntu wpa_supplicant[1112]: WPA: Key negotiation completed with 00:25:9c:5e:82:3d [PTK=TKIP GTK=TKIP]
Aug 25 10:48:49 gamer-ubuntu wpa_supplicant[1112]: CTRL-EVENT-CONNECTED - Connection to 00:25:9c:5e:82:3d completed (auth) [id=0 id_str=]
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> (ra0): supplicant connection state:  group handshake -> completed
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Philly'.
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) started...
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> (ra0): device state change: 5 -> 7 (reason 0)
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> dhclient started with pid 1809
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) complete.
Aug 25 10:48:49 gamer-ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Aug 25 10:48:49 gamer-ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium.
Aug 25 10:48:49 gamer-ubuntu dhclient: All rights reserved.
Aug 25 10:48:49 gamer-ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 25 10:48:49 gamer-ubuntu dhclient: 
Aug 25 10:48:49 gamer-ubuntu NetworkManager[709]: <info> (ra0): DHCPv4 state changed nbi -> preinit
Aug 25 10:48:49 gamer-ubuntu dhclient: Listening on LPF/ra0/98:fc:11:c3:8a:ac
Aug 25 10:48:49 gamer-ubuntu dhclient: Sending on   LPF/ra0/98:fc:11:c3:8a:ac
Aug 25 10:48:49 gamer-ubuntu dhclient: Sending on   Socket/fallback
Aug 25 10:48:49 gamer-ubuntu dhclient: DHCPREQUEST of 10.9.8.107 on ra0 to 255.255.255.255 port 67
Aug 25 10:48:49 gamer-ubuntu dhclient: DHCPACK of 10.9.8.107 from 10.9.8.1
Aug 25 10:48:49 gamer-ubuntu dhclient: bound to 10.9.8.107 -- renewal in 21417 seconds.

```

---

### Post by kai4785 on 2011-08-30
Ok, my problem ended up being a signal issue. Did a little site-survey, and found that my wireless adapter in my PC was not getting a good signal. Made some adjustments to where the PC was sitting (and facing), and I can connect to both AP's just fine now.

---

