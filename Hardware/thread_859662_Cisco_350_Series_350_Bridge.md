---
title: "Cisco 350 Series 350 Bridge"
date: 2008-07-14
forum: Hardware
---

### Post by mariom48 on 2008-07-14
Hello Forum,

I hope somebody can shed some light on this problem and also I hope I reach the proper forum for it.

I have a Cisco 350 Bridge which I use as an Access point, in previous Linux versions i was able to access my internal network and out to the internet with no problems and even as of now if I used my windows machine to connect I have no problem.

But now that I am using the 8.04 Ubuntu and other recent Linux versions of other distros iam having the same problem. So far I am sticking to Ubuntu i like it more. is user friendly my kids like love it which is the reason why i need to get a solution for it.

here are some messagess from wpa_supplicant log and messages log:

1) WPA Supplicant log

Trying to associate with 00:40:96:57:15:aa (SSID='****' freq=2437 MHz)
Authentication with 00:40:96:57:15:aa timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:40:96:57:15:aa (SSID='****' freq=2437 MHz)
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:40:96:57:15:aa (SSID='****' freq=2437 MHz)
Authentication with 00:40:96:57:15:aa timed out.
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:40:96:57:15:aa (SSID='****' freq=2437 MHz)
CTRL-EVENT-SCAN-RESULTS 
Authentication with 00:00:00:00:00:00 timed out.


Now from messages log:

Jul 14 16:36:33 localhost NetworkManager: <info>  Activation (wlan0) starting connection '****'
Jul 14 16:36:33 localhost NetworkManager: <info>  (wlan0): device state change: 3 -> 4
Jul 14 16:36:33 localhost NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 14 16:36:33 localhost NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 14 16:36:33 localhost NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 14 16:36:33 localhost NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 14 16:36:33 localhost NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 14 16:36:33 localhost NetworkManager: <info>  (wlan0): device state change: 4 -> 5
Jul 14 16:36:33 localhost NetworkManager: <info>  Activation (wlan0/wireless): connection '****' has security, and secrets exist.  No new secrets needed.
Jul 14 16:36:33 localhost NetworkManager: <info>  Config: added 'ssid' value '****'
Jul 14 16:36:33 localhost NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jul 14 16:36:33 localhost NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jul 14 16:36:33 localhost NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Jul 14 16:36:33 localhost NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Jul 14 16:36:33 localhost NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
Jul 14 16:36:33 localhost NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 14 16:36:33 localhost NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0
Jul 14 16:36:33 localhost NetworkManager: <info>  Config: set interface ap_scan to 1
Jul 14 16:36:33 localhost NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2
Jul 14 16:36:37 localhost netplugd[1919]: No interface name
Jul 14 16:36:37 localhost netplugd[1919]: Callback failed

DOES ANYBODY HAVE ANY IDEA? PLEASE HELP ME OUT WITH THIS PROBLEM.
I like to know what is the problem so I can be able to connect.

By the way if I used a Linksys wireless router it works.
Thank you very much.
Regards,
Mario

---

