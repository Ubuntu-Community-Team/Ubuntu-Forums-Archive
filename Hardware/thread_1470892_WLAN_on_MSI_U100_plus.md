---
title: "WLAN on MSI U100 plus"
date: 2010-05-03
forum: Hardware
---

### Post by Laurenz.Lanik on 2010-05-03
I own a MSI U100 plus netbook with a rt2700e wlan chip.
Ubuntu 9.10 ran without any problems (according to WLAN).

When I boot ubuntu 10.04 from USB-Stick, I very seldom get a connection to my WLAN.
I checked the drivers with lsmod, - it is the rt2860sta.

Password and settings are ok, because sometimes the WLAN could be connected to.
You can see an unsuccessful connection from /var/log/syslog here:

-----------------------------------------------------------------------
[SIZE=2]May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto llvie'
May  2 09:48:18 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  2 09:48:18 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto llvie' has security, but secrets are required.
May  2 09:48:18 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  2 09:48:18 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  2 09:48:18 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto llvie' has security, and secrets exist.  No new secrets needed.
May  2 09:48:18 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'llvie'
May  2 09:48:18 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May  2 09:48:18 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May  2 09:48:18 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
May  2 09:48:18 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  2 09:48:18 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  2 09:48:18 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  2 09:48:18 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
May  2 09:48:18 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
May  2 09:48:18 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning


May  2 09:48:23 ubuntu kernel: [  414.448570] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 756
May  2 09:48:23 ubuntu kernel: [  414.449166] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=3)
May  2 09:48:23 ubuntu wpa_supplicant[2715]: Trying to associate with 00:24:01:2b:77:b2 (SSID='llvie' freq=2422 MHz)
May  2 09:48:23 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  2 09:48:23 ubuntu wpa_supplicant[2715]: Association request to the driver failed

May  2 09:48:28 ubuntu wpa_supplicant[2715]: Authentication with 00:24:01:2b:77:b2 timed out.
May  2 09:48:28 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
May  2 09:48:28 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning

May  2 09:48:33 ubuntu wpa_supplicant[2715]: Trying to associate with 00:24:01:2b:77:b2 (SSID='llvie' freq=2422 MHz)
May  2 09:48:33 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  2 09:48:33 ubuntu kernel: [  424.465193] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 479
May  2 09:48:33 ubuntu kernel: [  424.465835] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=3)
May  2 09:48:33 ubuntu wpa_supplicant[2715]: Association request to the driver failed
May  2 09:48:34 ubuntu NetworkManager: <info>  wlan0: link timed out.[/SIZE]
-----------------------------------------------------------------------

Sometimes it connects, then the log looks like:
-----------------------------------------------------------------------
May  2 11:44:11 ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto llvie'
May  2 11:44:11 ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
May  2 11:44:11 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  2 11:44:11 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  2 11:44:11 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  2 11:44:11 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  2 11:44:11 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  2 11:44:11 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May  2 11:44:11 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto llvie' has security, but secrets are required.
May  2 11:44:11 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
May  2 11:44:11 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  2 11:44:12 ubuntu kernel: [  163.422633] composite sync not supported
May  2 11:44:16 ubuntu kernel: [  166.942223] composite sync not supported
May  2 11:44:19 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May  2 11:44:19 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May  2 11:44:19 ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
May  2 11:44:19 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May  2 11:44:19 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May  2 11:44:19 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May  2 11:44:19 ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
May  2 11:44:19 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto llvie' has security, and secrets exist.  No new secrets needed.
May  2 11:44:19 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'llvie'
May  2 11:44:19 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May  2 11:44:19 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May  2 11:44:19 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
May  2 11:44:19 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  2 11:44:19 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  2 11:44:19 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  2 11:44:19 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
May  2 11:44:19 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
May  2 11:44:24 ubuntu wpa_supplicant[2715]: Trying to associate with 00:24:01:2b:77:b2 (SSID='llvie' freq=2422 MHz)
May  2 11:44:24 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  2 11:44:24 ubuntu kernel: [  174.772115] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 517
May  2 11:44:24 ubuntu kernel: [  174.772639] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=3)
May  2 11:44:24 ubuntu wpa_supplicant[2715]: Association request to the driver failed
May  2 11:44:24 ubuntu wpa_supplicant[2715]: Associated with 00:24:01:2b:77:b2
May  2 11:44:24 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
May  2 11:44:27 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
May  2 11:44:27 ubuntu wpa_supplicant[2715]: WPA: Key negotiation completed with 00:24:01:2b:77:b2 [PTK=CCMP GTK=TKIP]
May  2 11:44:27 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
May  2 11:44:27 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
May  2 11:44:27 ubuntu NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'llvie'.
May  2 11:44:27 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
May  2 11:44:27 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
May  2 11:44:27 ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
May  2 11:44:27 ubuntu NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
May  2 11:44:27 ubuntu wpa_supplicant[2715]: CTRL-EVENT-CONNECTED - Connection to 00:24:01:2b:77:b2 completed (auth) [id=0 id_str=]
May  2 11:44:27 ubuntu NetworkManager: <info>  dhclient started with pid 11951
...
-----------------------------------------------------------------------

Any ideas ?

Laurenz

---

### Post by Laurenz.Lanik on 2010-05-05
Does nobody has the same problems ?

---

### Post by wagnus on 2010-05-06
I have almost the exact same problems with the msi u100, the RT2700E and kubuntu 10.04, but I haven't found a solution yet.

---

### Post by adostes on 2010-05-22
Same problem here, no solution yet. Maybe it's the wpa...

---

### Post by Laurenz.Lanik on 2010-05-23
It seems to be the drivers. - I installed the 2.6.33 kernel and it worked !!!

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

---

### Post by caporaso on 2010-06-06
Hi, Could you post instructions for installing the new kernel? it doesn't look like it's in the repositories yet.

Thanks!
Greg

---

### Post by anothermikemiller on 2010-07-08
Here is a link for the install directions:

[http://www.khattam.info/2010/02/06/installing-kernel-2-6-33-to-lucid-lynx-ubuntu-10-04-without-compiling/](http://www.khattam.info/2010/02/06/installing-kernel-2-6-33-to-lucid-lynx-ubuntu-10-04-without-compiling/)

Pretty easy, though: Download the headers x-all, x-generic (86/64), x-image and install in that order. Double click should open gdebi and hit the button.

---

