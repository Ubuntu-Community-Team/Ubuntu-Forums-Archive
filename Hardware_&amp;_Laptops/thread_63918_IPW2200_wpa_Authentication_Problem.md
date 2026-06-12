---
title: "IPW2200 wpa Authentication Problem"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by Mint Sauce on 2005-09-09
First post so hullo all!

I only installed kubuntu yesterday (first linux install) and i've followed [THIS]([URL=http://www.ubuntuforums.org/showthread.php?t=26623&highlight=apt)]THIS[/URL]to to get my wlan setup, messed with all the configs that might help me connect, but according to kwifi my pc authenicates and then drops, over and over

dmesg | grep ipw:

```

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: failed to send CARD_DISABLE command
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.

```
I have no idea what to do so has anyone got any suggestions. Tried search but i can't find anything specific to my problem. Thanks.

If you need any log, errors or whatever please tell me the command to obtain it (cus i sux0r at linux :D..... atm anywho)

.:EDIT:.
[THIS](http://ipw2200.sourceforge.net/faq.php#qa_1_1) would suggest that i need [THIS](http://rfswitch.sourceforge.net/)? My laptop has a switch to change wlan status (turn it on/off), is this needed?  :? The switch works too btw!

.:edit2:.
iwconfig show various out puts depending on whether it's just dropped, or just autenticated (never stable tho). Anyhoo i just got this output

```
eth1      IEEE 802.11g  ESSID:"Willorie"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:F5:54:0B:59
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=90/100  Signal level=-39 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:18   Missed beacon:6
```

The encyption key:off is what i'm worried about. 

wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
       ssid="Willorie"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       psk="J7DHEN58KN"
}
```

Also the encoding when this file is saved is set to utf8, is that correct?

Thanks.

.:edit3:.

dmesg grep | ipw:

```
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: failed to send CARD_DISABLE command
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
ipw2200: Firmware error detected.  Restarting.
```

This wasn't happening before. Sorry this post is getting long, but i really need to get this working, any ideas? TIA.

PS: Didn't see the networking forum, sorry can a mod move this thread please. Ta.

.:edit:.
I've just read another thread (i'm onto the random reading stage of problem solving) and it suggested that my wifi manager could be at fault, i'm using KWiFiManager. Can anyone suggest a good alternative- pref gui as i'd like to have an icon in the systray(or whatever it's called in linux). Ta again.

.:edit:.
Noticed something when i ran wpa_supplicant:

```

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=8):
     57 69 6c 6c 6f 72 69 65                           Willorie
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 11: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='Willorie'
Daemonize..

```

Whats this (from above output) > ```
line 11;removed ccmp from group cipher list since it was not allowed for pairwise cipher
```

---

