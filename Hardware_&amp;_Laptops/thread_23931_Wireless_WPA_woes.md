---
title: "Wireless WPA woes"
date: 2005-04-04
forum: Hardware &amp; Laptops
---

### Post by crash75uk on 2005-04-04
I'm desperately attemtping to get my wireless card working in Ubuntu with Wpa.  

I have a US Robotics 805410 wireless card and a network using Wpa-psk

My wpa_supplicant file is set up as follows:

# Only WPA-PSK is used. Any valid cipher combination is accepted.
network={
	ssid="USR8054"
	scan_ssid=1
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise=CCMP TKIP
	group=CCMP TKIP
	key_mgmt=WPA-PSK
	psk="verysecretpassword"
}

but when i attaempt to run the wpa_supplicant command:

wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -dd

i get the results

Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 12 - start of a new network block
ssid - hexdump_ascii(len=7):
     55 53 52 38 30 35 34                              USR8054
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=15): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='USR8054'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: 00:c0:49:ee:87:62
wpa_driver_hostap_set_wpa: enabled=1
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_countermeasures: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=7):
     55 53 52 38 30 35 34                              USR8054
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Scan timeout - try to get results
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
No suitable AP found.
Setting scan request: 5 sec 0 usec
Signal 2 received - terminating
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_hostap_set_wpa: enabled=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
wpa_driver_hostap_set_drop_unencrypted: enabled=0
wpa_driver_hostap_set_countermeasures: enabled=0


Can anyone shed any light on what's going on, is the problem with wpa, the hardware or my router.

Jamie

---

### Post by luca_linux on 2005-04-12
What driver are you using for your wireless card? Anyway you have to specify it.
For example I have an ipw2200 and I have to type this:
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd

---

