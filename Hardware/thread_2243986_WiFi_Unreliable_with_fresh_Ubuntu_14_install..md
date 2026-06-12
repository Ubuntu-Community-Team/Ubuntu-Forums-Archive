---
title: "WiFi Unreliable with fresh Ubuntu 14 install."
date: 2014-09-12
forum: Hardware
---

### Post by jennifer7 on 2014-09-12
Need help with my wireless connection. It worked great when I had Win8, but Win8 is horrible. I didn't do a dual boot, so Ubuntu is the only OS on this laptop.


```
########## wireless info START ##########


Report from: 12 Sep 2014 11:11 CDT -0500


Script from: 05 Sep 2014 22:42 UTC +0000


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0181]
    Kernel driver in use: rtl8188ee


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 10f1:1a52 Importek 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


rtl8188ee 89677 0 
rtl_pci 26690 1 rtl8188ee
rtlwifi 63475 2 rtl_pci,rtl8188ee
mac80211 630653 3 rtl_pci,rtlwifi,rtl8188ee
cfg80211 484040 2 mac80211,rtlwifi
wmi 19177 1 toshiba_acpi


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0 Link encap:Ethernet HWaddr <MAC addr eth0> 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


wlan0 Link encap:Ethernet HWaddr <MAC addr wlan0> 
inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::42f0:2fff:fee9:fb2d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:150254 errors:0 dropped:2 overruns:0 frame:0
TX packets:138329 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:68121387 (68.1 MB) TX bytes:19214628 (19.2 MB)


##### iwconfig #####


eth0 no wireless extensions.


lo no wireless extensions.


wlan0 IEEE 802.11bgn ESSID:"Home" 
Mode:Managed Frequency:2.462 GHz Access Point: <MAC addr Home> 
Bit Rate=18 Mb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thr=2347 B Fragment thr:off
Power Management:off
Link Quality=70/70 Signal level=22 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:3 Missed beacon:0


##### route #####


Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 wlan0
192.168.1.0 0.0.0.0 255.255.255.0 U 9 0 0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1
search no.cox.net


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: r8169
State: unavailable
Default: no
HW Address: <MAC addr eth0>


Capabilities:
Carrier Detect: yes


Wired Properties
Carrier: off


- Device: wlan0 [Home] --------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl8188ee
State: connected
Default: yes
HW Address: <MAC addr wlan0>


Capabilities:
Speed: 18 Mb/s


Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes


Wireless Access Points (* = current AP)
2WIRE758: Infra, <MAC addr 2WIRE758>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
2WIRE371: Infra, <MAC addr 2WIRE371>, Freq 2422 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
2WIRE201: Infra, <MAC addr 2WIRE201>, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
ATT9XKAipi: Infra, <MAC addr ATT9XKAipi>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
*Home: Infra, <MAC addr Home>, Freq 2462 MHz, Rate 54 Mb/s, Strength 63


IPv4 Settings:
Address: 192.168.1.101
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1


DNS: 68.105.28.11
DNS: 68.105.29.11
DNS: 68.105.28.12


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels #####


eth0 no frequency information.


lo no frequency information.


wlan0 13 channels in total; available frequencies :
Channel 01 : 2.412 GHz
Channel 02 : 2.417 GHz
Channel 03 : 2.422 GHz
Channel 04 : 2.427 GHz
Channel 05 : 2.432 GHz
Channel 06 : 2.437 GHz
Channel 07 : 2.442 GHz
Channel 08 : 2.447 GHz
Channel 09 : 2.452 GHz
Channel 10 : 2.457 GHz
Channel 11 : 2.462 GHz
Channel 12 : 2.467 GHz
Channel 13 : 2.472 GHz
Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #####


Channel occupancy:


2 WLAPs on Frequency:2.422 GHz (Channel 3)
2 WLAPs on Frequency:2.437 GHz (Channel 6)
1 WLAPs on Frequency:2.462 GHz (Channel 11)


eth0 Interface doesn't support scanning.


lo Interface doesn't support scanning.


wlan0 Scan completed :
Cell 01 - Address: <MAC addr Home>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=50/70 Signal level=-60 dBm 
Encryption key:off
ESSID:"Home"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000000fbe4efbd2
Extra: Last beacon: 20ms ago
Cell 02 - Address: <MAC addr 2WIRE371>
Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=46/70 Signal level=-64 dBm 
Encryption key:on
ESSID:"2WIRE371"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000567b463463d
Extra: Last beacon: 20ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 03 - Address: <MAC addr 2WIRE201>
Channel:3
Frequency:2.422 GHz (Channel 3)
Quality=38/70 Signal level=-72 dBm 
Encryption key:on
ESSID:"2WIRE201"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000026e2ab69109
Extra: Last beacon: 20ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 04 - Address: <MAC addr ATT9XKAipi>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=68/70 Signal level=-42 dBm 
Encryption key:on
ESSID:"ATT9XKAipi"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00000010f108e11a
Extra: Last beacon: 20ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 05 - Address: <MAC addr 2WIRE758>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=66/70 Signal level=-44 dBm 
Encryption key:on
ESSID:"2WIRE758"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000001700b144b37
Extra: Last beacon: 20ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK


##### module infos #####


[rtl8188ee]
filename: /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware: rtlwifi/rtl8188efw.bin
description: Realtek 8188E 802.11n PCI wireless
license: GPL
author: Larry Finger    <Larry.Finger@lwfinger.net>
author: Realtek WlanFAE    <wlanfae@realtek.com>
author: zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion: FA356D8EFD887B567263405
depends: rtlwifi,rtl_pci,mac80211
intree: Y
vermagic: 3.13.0-35-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo: sha512
parm: swenc:Set to 1 for software crypto (default 0)
(bool)
parm: ips:Set to 0 to not use link power save (default 1)
(bool)
parm: swlps:Set to 1 to use SW control power save (default 0)
(bool)
parm: fwlps:Set to 1 to use FW control power save (default 1)
(bool)
parm: msi:Set to 1 to use MSI interrupts mode (default 0)
(bool)
parm: debug:Set debug level (0-5) (default 0) (int)


[rtl_pci]
filename: /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description: PCI basic driver for rtlwifi
license: GPL
author: Larry Finger    <Larry.FInger@lwfinger.net>
author: Realtek WlanFAE    <wlanfae@realtek.com>
author: lizhaoming    <chaoming_li@realsil.com.cn>
srcversion: D5E4890DC428FA5A1BF92DF
depends: mac80211,rtlwifi
intree: Y
vermagic: 3.13.0-35-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo: sha512


[rtlwifi]
filename: /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description: Realtek 802.11n PCI wireless core
license: GPL
author: Larry Finger    <Larry.FInger@lwfinger.net>
author: Realtek WlanFAE    <wlanfae@realtek.com>
author: lizhaoming    <chaoming_li@realsil.com.cn>
srcversion: E1F4663325225EE8DBA54CA
depends: mac80211,cfg80211
intree: Y
vermagic: 3.13.0-35-generic SMP mod_unload modversions 
signer: Magrathea: Glacier signing key
sig_key: B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo: sha512


##### module parameters #####


[rtl8188ee]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N


##### /etc/modules #####


lp
rtc


##### blacklists #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


##### rc.local #####


[ -x /usr/bin/numlockx ] && numlockx on


exit 0


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[32640.867865] wlan0: deauthenticated from <MAC addr Home> (Reason: 7)
[32640.876050] wlan0: authenticate with <MAC addr Home>
[32640.876273] wlan0: send auth to <MAC addr Home> (try 1/3)
[32640.878238] wlan0: authenticated
[32640.878701] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[32640.878721] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[32640.882312] wlan0: associate with <MAC addr Home> (try 1/3)
[32640.884335] wlan0: RX AssocResp from <MAC addr Home> (capab=0x401 status=0 aid=7)
[32640.884469] wlan0: associated
[32707.004766] wlan0: deauthenticated from <MAC addr Home> (Reason: 7)
[32707.038629] wlan0: authenticate with <MAC addr Home>
[32707.038836] wlan0: send auth to <MAC addr Home> (try 1/3)
[32707.046400] wlan0: authenticated
[32707.047231] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[32707.047243] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[32707.050399] wlan0: associate with <MAC addr Home> (try 1/3)
[32707.052485] wlan0: RX AssocResp from <MAC addr Home> (capab=0x401 status=0 aid=7)
[32707.052622] wlan0: associated
[32742.775713] wlan0: deauthenticating from <MAC addr Home> by local choice (reason=3)
[32747.297939] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[32749.015099] wlan0: authenticate with <MAC addr Home>
[32749.024739] wlan0: send auth to <MAC addr Home> (try 1/3)
[32749.026689] wlan0: authenticated
[32749.027698] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[32749.027707] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[32749.030386] wlan0: associate with <MAC addr Home> (try 1/3)
[32749.032400] wlan0: RX AssocResp from <MAC addr Home> (capab=0x401 status=0 aid=7)
[32749.032516] wlan0: associated
[32749.032556] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[32749.034478] wlan0: deauthenticating from <MAC addr Home> by local choice (reason=2)
[32749.058473] wlan0: authenticate with <MAC addr Home>
[32749.058597] wlan0: send auth to <MAC addr Home> (try 1/3)
[32749.060198] wlan0: authenticated
[32749.062581] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[32749.062589] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[32749.069585] wlan0: associate with <MAC addr Home> (try 1/3)
[32749.071528] wlan0: RX AssocResp from <MAC addr Home> (capab=0x401 status=0 aid=7)
[32749.071647] wlan0: associated
[32759.074489] wlan0: deauthenticating from <MAC addr Home> by local choice (reason=3)
[32760.424549] wlan0: authenticate with <MAC addr Home>
[32760.433346] wlan0: send auth to <MAC addr Home> (try 1/3)
[32760.437856] wlan0: authenticated
[32760.439521] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[32760.439530] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[32760.442852] wlan0: associate with <MAC addr Home> (try 1/3)
[32760.448106] wlan0: RX AssocResp from <MAC addr Home> (capab=0x401 status=0 aid=7)
[32760.448241] wlan0: associated


########## wireless info END ############
```

---

### Post by dave131 on 2014-09-12
See if this helps - it's for the same adapter and similar problems:

[http://askubuntu.com/questions/463030/wireless-not-connecting-dropping-connection](http://askubuntu.com/questions/463030/wireless-not-connecting-dropping-connection)

---

### Post by jennifer7 on 2014-09-14
It's not an adapter. It's a wireless NIC pre-installed on my Toshiba Satellite C55-A5105 laptop. I tried it anyway, but it didn't work. Anything else I could try?

---

### Post by varunendra on 2014-09-14
Hello Jennifer, Welcome to the forums! :)

First of all, please edit your first post to wrap the script report part within 'Code' tags to make it cleaner, compact and more readable. Please follow the "Use Code Tags" link in my signature below to see how.

Regarding the problem, please try a driver parameter first. Open a terminal (Ctrl-Alt-T) and run the following code in it -
```
echo "options rtl8188ee fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8188ee.conf
```
Reboot, reconnect and let us know if it is any more stable now. Thanks.

**PS:**
Checked the link from dave after writing the above suggestion. Basically it is the same thing as suggested above, only with the native driver. If it fails, please try what is suggested in that link, that would be my **next** suggestion as well, if required.

---

### Post by jennifer7 on 2014-09-14
As I stated in my previous post, I've already tried what he posted. It didn't work. Which is why I'm asking for more help now. ^.^ I'll try this and get back to you.

---

### Post by dave131 on 2014-09-15
> **jennifer7 said:**
> It's not an adapter. It's a wireless NIC pre-installed on my Toshiba Satellite C55-A5105 laptop. I tried it anyway, but it didn't work. Anything else I could try?

Sorry if that was confusing.  Even an integrated wireless NIC is an adapter.  I just use that so as to not have to worry about internal vs external (usb dongle, etc.) adapters.

Sorry! ;)

---

