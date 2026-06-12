---
title: "Issue with Qualcomm Atheros AR9485 Wireless Network Adapter"
date: 2015-06-28
forum: Hardware
---

### Post by siugh on 2015-06-28
Hi,
I am using Ubuntu 14.04 64bit.
My laptop is ASUS X551CAP
My wireless adapter doesn't work at all.
I already solved the "hard locked" issue with:

[PHP]root@notebook-asus:/etc/modprobe.d# cat asus_nb_wmi.confoptions asus_nb_wmi wapf=4
[/PHP]

so now wlan0 can be in "up" state.
Anyway, I am not able to connect to any wifi network, even with no security at all.

I tried with backports driver (from kernel 3.16).
Compilation ends fine, module is loaded but the problem isn't solved.

Any idea?

[PHP]root@notebook-asus:~# cat wireless-info.txt
        ======== Wireless-Info START ========
System-Info ~~~~~~~~~~~~~~~~~~~~~~~~
notebook-asus 3.13.0-45-generic x86_64,  Ubuntu 14.04.2 LTS, trusty
CPU    : Intel(R) Celeron(R) CPU 1007U @ 1.50GHzMemory : 3839 MBUptime : 21:43:54 up 16 min,  2 users,  load average: 0,27, 0,25, 0,21

lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)        Subsystem: AzureWave Device [1a3b:2c97]        Kernel driver in use: ath9k--03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)        Subsystem: ASUSTeK Computer Inc. Device [1043:200f]        Kernel driver in use: r8169

lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 001 Device 004: ID 04f2:b404 Chicony Electronics Co., LtdBus 001 Device 005: ID 13d3:3362 IMC NetworksBus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 003 Device 002: ID 045e:0797 Microsoft Corp.Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~
wlan0     IEEE 802.11bgn  ESSID:off/any          Mode:Managed  Access Point: Not-Associated   Tx-Power=off          Retry  long limit:7   RTS thr:off   Fragment thr:off          Encryption key:off          Power Management:off


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
      Interface               Soft blocked  Hard blocked0: phy0: Wireless LAN             no            yes1: asus-wlan: Wireless LAN        no            no2: asus-bluetooth: Bluetooth      no            no3: hci0: Bluetooth                no            no

lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
asus_nb_wmi            16990  0asus_wmi               24191  1 asus_nb_wmisparse_keymap          13948  1 asus_wmiath9k                 164164  0ath9k_common           13551  1 ath9kath9k_hw              453856  2 ath9k_common,ath9kath                    28698  3 ath9k_common,ath9k,ath9k_hwmac80211              630669  1 ath9kcfg80211              484040  3 ath,ath9k,mac80211wmi                    19177  1 asus_wmivideo                  19476  2 i915,asus_wmi

module parameters ~~~~~~~~~~~~~~~~~~
asus_nb_wmi   (1): wapf=0ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1wmi           (2): debug_dump_wdg=N | debug_event=N

nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
State: connected (global)================================o=========  ====o========o=============o=========o===========o  ==============o=========== Interface & ID                 | Type        | Driver | State       | Default | Speed     | Support      | HW Addr================================o=============  o========o=============o=========o===========o====  ==========o=========== eth0  [Connessione via cavo 1] | Wired       | r8169  | connected   | yes     | 100 Mb/s  |              | <MAC eth0>
    Address:         192.168.1.12    Prefix:          24 (255.255.255.0)    Gateway:         192.168.1.1    DNS:             8.8.8.8    DNS:             8.8.4.4--------------------------------+-------------+--------+-------------+---------+-----------+--------------+----------- wlan0                          | 802.11 WiFi | ath9k  | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>--------------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------

NetworkManager.state ~~~~~~~~~~~~~~~[main]NetworkingEnabled=trueWirelessEnabled=trueWWANEnab  led=trueWimaxEnabled=true

NetworkManager.conf ~~~~~~~~~~~~~~~~
[main]plugins=ifupdown,keyfile,ofonodns=dnsmasq
[ifupdown]managed=false

NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~
# interfaces(5) file used by ifup(8) and ifdown(8)auto loiface lo inet loopback
resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~
nameserver 127.0.1.1

Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~
Tabella di routing IP del kernelDestination     Gateway         Genmask         Flags Metric Ref    Use Iface0.0.0.0         192.168.1.1   0.0.0.0         UG    0      0        0 eth0192.168.1.0   0.0.0.0         255.255.255.0 U     1      0        0 eth0


--- 127.0.1.1 ping statistics ---2 packets transmitted, 2 received, 0% packet loss, time 999msrtt min/avg/max/mdev = 0.040/0.047/0.054/0.007 ms

iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~
(Region : "it_IT.UTF-8")country 00:        (2402 - 2472 @ 40), (3, 20)        (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS        (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS        (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS        (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~
wlan0     14 channels in total; available frequencies :          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~
[/etc/modprobe.d/blacklist-ath_pci.conf]blacklist ath_pci

modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[asus_nb_wmi]filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/asus-nb-wmi.kosrcversion:     67514DF02FC4A206C47D0F5depends:        asus-wmiparm:           wapf:WAPF value (uint)
[asus_wmi]filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/asus-wmi.kosrcversion:     222BD5E26B3EE82CC433FF2depends:        sparse-keymap,wmi,video
[ath9k]filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.kosrcversion:     EABAC052C3DF339FA6E716Cdepends:        ath9k_hw,mac80211,ath9k_common,cfg80211,athparm:           debug:Debugging mask (uint)parm:           nohwcrypt:Disable hardware encryption (int)parm:           blink:Enable LED blink on activity (int)parm:           btcoex_enable:Enable wifi-BT coexistence (int)parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)parm:           ps_enable:Enable WLAN PowerSave (int)
[ath9k_common]filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.kosrcversion:     5ED2DF2BD124A3813829DA8depends:        ath,ath9k_hw
[ath9k_hw]filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.kosrcversion:     94B3813AF84C49B115229ADdepends:        ath
[ath]filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath.kosrcversion:     88A67C5359B02C5A710AFCFdepends:        cfg80211
[mac80211]filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.kosrcversion:     385697223F8285F67C93A06depends:        cfg80211parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
[cfg80211]filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.kosrcversion:     C2478077E22138832B71659depends:parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
[wmi]filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/wmi.kosrcversion:     CED5410F008DC70DF5F064Bdepends:parm:           debug_event:Log WMI Events [0/1] (bool)parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)
[video]filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/acpi/video.kosrcversion:     FD364E86295EDCA7831C8FBdepends:parm:           brightness_switch_enabled:boolparm:           allow_duplicates:boolparm:           use_native_backlight:int

udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~
# PCI device 0x10ec:0x8136 (r8169)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

Custom files/entries ~~~~~~~~~~~~~~~
/etc/modules        : Default/etc/rc.local       : Default/etc/modprobe.d     : Not Default/etc/pm/(cnf|pw|sl) : Default
[/etc/modprobe.d]iwlwifi.conf      : remove iwlwifi \                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \                    && /sbin/modprobe -r mac80211mlx4.conf         : softdep mlx4_core post: mlx4_en

Kernel boot line ~~~~~~~~~~~~~~~~~~~
BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic.efi.signed root=UUID=0851a40e-7825-430d-867c-11d4ed9414ec ro

dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[    0.752885] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba[    0.753239] audit: initializing netlink socket (disabled)[    1.124827] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded[    1.725979] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f00)[   14.819151] wmi: Mapper loaded[   14.993169] ath: phy0: Disable PLL PowerSave[   15.000995] ath: EEPROM regdomain: 0x60[   15.000999] ath: EEPROM indicates we should expect a direct regpair map[   15.001002] ath: Country alpha2 being used: 00[   15.001003] ath: Regpair used: 0x60[   15.321001] asus_wmi: ASUS WMI generic driver loaded[   15.322725] asus_wmi: Initialization: 0x1[   15.322767] asus_wmi: BIOS WMI version: 7.9[   15.322816] asus_wmi: SFUN value: 0x4a0877[   15.325036] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input14[   15.423431] asus_wmi: Backlight controlled by ACPI video driver[   17.119751] Bluetooth: BNEP (Ethernet Emulation) ver 1.3[   18.623752] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[   18.627202] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
        ======== Done ========root@notebook-asus:~#[/PHP]

---

### Post by jeremy31 on 2015-06-29
Run the script again now that the wapf=4 parameter is set and paste the contents of the wireless-info file using [ code ] [ /code ] tags without the spaces as the formatting is lost using the PHP code tags

---

