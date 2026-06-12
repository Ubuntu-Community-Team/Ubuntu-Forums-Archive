---
title: "Can't make RTL8188CE work with hostapd (rtl8192ce)"
date: 2012-07-16
forum: Hardware
---

### Post by XabiX on 2012-07-16
Hello,

I am trying to setup a wireless hotspot with my xs36v barbone (running Precise 12.04 i386). Unfortunately when I start hostapd, I have got the following error:

hostapd -dd /etc/hostapd/hostapd.conf
> Configuration file: /etc/hostapd/hostapd.conf
nl80211: Add own interface ifindex 3
nl80211: Add own interface ifindex 4
nl80211: New interface mon.wlan0 created: ifindex=8
nl80211: Add own interface ifindex 8
Could not set interface mon.wlan0 flags: Operation not possible due to RF-kill
nl80211: Remove interface ifindex=8
nl80211: Failed to set interface wlan0 into AP mode
nl80211 driver initialization failed.
ELOOP: remaining socket: sock=4 eloop_data=0x842e900 user_data=0x842eeb0 handler=0x807c5e0
ELOOP: remaining socket: sock=6 eloop_data=0x8430cb8 user_data=(nil) handler=0x8086770

I tried with different drivers like mac80211.

I did install the drivers from Realtek website (rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011) and the latest linux-firmware_1.84_all.deb

But I can't make it work for any reason. Any help would be welcome. Do I need to move to a newest kernel to make it work?

Thanks
XabiX

lspci
> 02:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

lsmod
> rtl8192ce              75491  0 
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95804  1 rtl8192ce
mac80211              436455  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              178679  2 rtlwifi,mac80211

modinfo rtl8192ce
> filename:       /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE <wlanfae@realtek.com>
author:         lizhaoming      <chaoming_li@realsil.com.cn>
srcversion:     18B9D7DE9AA317668E0197D
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       3.2.0-26-generic SMP mod_unload modversions 686 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)

/etc/hostapd/hostapd.conf 
> interface=wlan0
driver=nl80211
bridge=br0
ssid=my ssid
hw_mode=g
channel=6
macaddr_acl=0
ignore_broadcast_ssid=0
auth_algs=1
wpa=2
wpa_passphrase=myPWDwithMOREthan8digits
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

nm-tool  NetworkManager Tool
> State: connected (global)
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             unmanaged
  Default:           no
  HW Address:        E0:91:53:6F:55:E7

  Capabilities:
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            jme
  State:             unmanaged
  Default:           no
  HW Address:        80:EE:73:31:54:B2

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on


rfkill list all
> 0: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no


iwconfig 
> lo        no wireless extensions.
br0       no wireless extensions.
wlan0     IEEE 802.11bgn  Mode:Master  Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
eth0      no wireless extensions.


/etc/network/interfaces
> auto lo br0
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet manual

allow-hotplug wlan0
iface wlan0 inet manual

iface br0 inet dhcp
bridge_ports eth0 wlan0

ifconfig
> br0       Link encap:Ethernet  HWaddr 80:ee:73:31:54:b2  
          inet addr:192.168.0.40  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::82ee:73ff:fe31:54b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1035011 (1.0 MB)  TX bytes:419797 (419.7 KB)

eth0      Link encap:Ethernet  HWaddr 80:ee:73:31:54:b2  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18312 errors:0 dropped:130 overruns:0 frame:0
          TX packets:2636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2148515 (2.1 MB)  TX bytes:414373 (414.3 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:329583 (329.5 KB)  TX bytes:329583 (329.5 KB)

---

### Post by XabiX on 2012-07-18
Any idea?

Merci:guitar:

---

