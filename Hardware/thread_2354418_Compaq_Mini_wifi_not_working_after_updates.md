---
title: "Compaq Mini wifi not working after updates"
date: 2017-03-02
forum: Hardware
---

### Post by craigivybryan on 2017-03-02
Hello All...I have an old Compaq Mini netbook that was running Ubuntu. I haven't used it in almost 12 months, so when I turned it on today I decided to run the updates that were pending. When it finally finished my wifi stopped working. Can't remember how I got it going last time so here I am. I ran the wireless script I found in another post provided by Arunendra, and here are the results:
```
########## wireless info START ##########

Report from: 02 Mar 2017 12:19 EST -0500

Booted last: 02 Mar 2017 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-65-generic #86-Ubuntu SMP Thu Feb 23 17:49:18 UTC 2017 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z049.00 Wireless Mini PCIe Card [103c:1507]
    Kernel driver in use: wl

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Hewlett-Packard Company AR8132 Fast Ethernet [103c:308f]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 001 Device 002: ID 10f1:1a13 Importek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wl                   6209536  0
cfg80211              499712  1 wl
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:10.7.209.164  Bcast:10.7.209.255  Mask:255.255.255.0
          inet6 addr: fe80::d95d:7f3f:2ddb:83fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13794 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:43562775 (43.5 MB)  TX bytes:1187271 (1.1 MB)

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:4175
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlp1s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.7.209.1      0.0.0.0         UG    100    0        0 enp2s0
10.7.209.0      0.0.0.0         255.255.255.0   U     100    0        0 enp2s0
10.60.253.50    10.7.209.1      255.255.255.255 UGH   100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search corp01.oct.on.ca

##### network managers ##################

Installed:

    NetworkManager

Running:

root       756     1  0 11:56 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8132 Fast Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       99ece089-0fb5-343d-83be-e3bc384e802f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   99ece089-0fb5-343d-83be-e3bc384e802f | Wired connection 1
IP4.ADDRESS[1]:                         10.7.209.164/24
IP4.GATEWAY:                            10.7.209.1
IP4.ROUTE[1]:                           dst = 10.60.253.50/32, nh = 10.7.209.1, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.1.253.3
IP4.DNS[2]:                             10.1.253.7
IP4.DNS[3]:                             10.1.253.40
IP4.DOMAIN[1]:                          corp01.oct.on.ca
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 10.1.253.3 10.1.253.7 10.1.253.40
DHCP4.OPTION[5]:                        ip_address = 10.7.209.164
DHCP4.OPTION[6]:                        filename = Boot\x64\wdsnbp.com
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 10.60.253.50
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 10.7.209.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 604800
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 10.7.209.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 345600
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = corp01.oct.on.ca
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1489165864
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 10.7.209.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 10.1.253.191
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 691200
IP6.ADDRESS[1]:                         fe80::d95d:7f3f:2ddb:83fa/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4312 802.11b/g LP-PHY (U98Z049.00 Wireless Mini PCIe Card)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.271 (r587334)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/OCTCouncil]] (600 root)
[connection] id=OCTCouncil | type=wifi | permissions=user:craig:;
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=OCTCouncil
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp2s0    no frequency information.

wlp1s0    32 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

wlp1s0    No scan results

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-65-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     0ADAE750C888A523D63D8B5
depends:        cfg80211
vermagic:       4.4.0-65-generic SMP mod_unload modversions 686 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-65-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A7DC879B6551813C20004F1
depends:        
intree:         Y
vermagic:       4.4.0-65-generic SMP mod_unload modversions 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

##### dmesg #############################

[    8.612278] wl: module license 'MIXED/Proprietary' taints kernel.
[    8.819351] wl: module verification failed: signature and/or required key missing - tainting kernel
[   10.615617] wlan0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   11.259832] wl 0000:01:00.0 wlp1s0: renamed from wlan0
[   30.140589] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready (repeated 2 times)
[   30.186373] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[  897.908325] atl1c 0000:02:00.0: atl1c: enp2s0 NIC Link is Up<100 Mbps Full Duplex>
[  897.908380] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[ 1395.511062] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

---

