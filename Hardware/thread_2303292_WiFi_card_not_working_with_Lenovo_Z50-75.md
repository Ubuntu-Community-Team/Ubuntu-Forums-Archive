---
title: "WiFi card not working with Lenovo Z50-75"
date: 2015-11-17
forum: Hardware
---

### Post by Mogrob on 2015-11-17
I just bought this laptop and tried to install Ubuntu 14.04.3. The installation went fine, but the wifi card is not detected. This is the first time something like this happens to me, so I have no idea how to debug the issue, let alone how to fix it. Googling didn't help, so I turned to the forum. The output of wireless_script is below. Any help would be much appreciated. Thank you!

```


########## wireless info START ##########

Report from: 17 Nov 2015 19:35 GMT +0000

Booted last: 17 Nov 2015 19:23 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3814]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
    Subsystem: Lenovo Device [17aa:3545]

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 174f:14be Syntek 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05dc:a815 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  1 ath9k
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:130.88.123.11  Bcast:130.88.123.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169128609 (169.1 MB)  TX bytes:4061263 (4.0 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         130.88.123.250  0.0.0.0         UG    0      0        0 eth0
130.88.123.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search man.ac.uk

##### network managers ##################

Installed:

    NetworkManager

Running:

root       892     1  0 19:22 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         130.88.123.11
    Prefix:          24 (255.255.255.0)
    Gateway:         130.88.123.250

    DNS:             130.88.203.7
    DNS:             130.88.13.7
    DNS:             130.88.200.6
    DNS:             130.88.94.110

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DFC03DD607884E899C8398C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-33-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:B4:3F:BA:F1:2F:D3:A0:26:57:73:E0:0E:22:F4:39:9F:63:4B:16
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   21.382311] r8169 0000:01:00.0 eth0: link down (repeated 2 times)
[   21.382411] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.055287] r8169 0000:01:00.0 eth0: link up
[   23.055307] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   54.845490] r8169 0000:01:00.0 eth0: link down
[  232.428460] r8169 0000:01:00.0 eth0: link up

########## wireless info END ############

```

---

### Post by jeremy31 on 2015-11-17
```
sudo apt-get install build-essential linux-headers-$(uname -r) git
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/09/03/backports-20150903.tar.gz
tar -zxvf backports-20150903.tar.gz
cd backports-20150903
make defconfig-ath10k
make
sudo make install
git clone https://github.com/atondwal/ath10k-firmware.git
sudo cp -r /ath10k-firmware/ath10k/ /lib/firmware/
sudo cp -r /lib/firmware/ath10k/QCA6164/hw2.1 /lib/firmware/ath10k/QCA6174/
```

Reboot

If you have other wireless cards that you might want to use(USB dongle) use ```
make defconfig-wifi
``` rather than ```
make defconfig-ath10k
```  in step 6 above.  I imagine you manually loaded ath9k thinking it might support this device

---

### Post by Mogrob on 2015-11-18
Hi [**[COLOR=#000000]jeremy31[/COLOR]**]("http://ubuntuforums.org/member.php?u=1924242"),
thank you very much for your help, your sequence of commands worked.
Yes, I had tried to load ath9k because I thought it was the module for atheros cards, I wasn't aware of the existence of a newer version (which is not part of the linux kernel yet, apparently).

---

