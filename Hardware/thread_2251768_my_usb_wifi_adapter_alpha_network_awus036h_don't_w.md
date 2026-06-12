---
title: "my usb wifi adapter alpha network awus036h don't work"
date: 2014-11-06
forum: Hardware
---

### Post by redsugar on 2014-11-06
Hello !

When i plug my adapter ,the del is blinking .
But it don't work 


how can i fix this ?


#dmesg

[  448.850004] usb 1-8: new high-speed USB device number 4 using ehci-pci
[  448.988458] usb 1-8: New USB device found, idVendor=0bda, idProduct=8187
[  448.988464] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  448.988467] usb 1-8: Product: RTL8187_Wireless
[  448.988469] usb 1-8: Manufacturer: Manufacturer_Realtek_RTL8187_
[  448.988471] usb 1-8: SerialNumber: 00C0CA7EFFCD
[  449.116135] cfg80211: Calling CRDA to update world regulatory domain
[  449.205706] cfg80211: World regulatory domain updated:
[  449.205713] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  449.205716] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  449.205718] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  449.205720] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  449.205722] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  449.205724] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  449.416407] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[  449.416655] ieee80211 phy0: hwaddr 00:c0:ca:7e:ff:cd, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  449.427552] rtl8187: Customer ID is 0xFF
[  449.428038] rtl8187: wireless switch is on
[  449.428064] usbcore: registered new interface driver rtl8187
[  451.383095] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  451.383599] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready




toto@toto-M2N6-XE ~ $ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


toto@toto-M2N6-XE ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:7b:9b:42  
          inet adr:192.168.1.18  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::21e:8cff:fe7b:9b42/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:463 erreurs:0 :0 overruns:0 frame:0
          TX packets:590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:286838 (286.8 KB) Octets transmis:81826 (81.8 KB)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          Packets reçus:246 erreurs:0 :0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:22590 (22.5 KB) Octets transmis:22590 (22.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:7e:ff:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)



toto@toto-M2N6-XE ~ $ sudo iwlist scan
[sudo] password for toto: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : No such device



toto@toto-M2N6-XE ~ $ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             unavailable
  Default:           no
  HW Address:        00:C0:CA:7E:FF:CD

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Ethernet automatique] -----------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:1E:8C:7B:9B:42

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



toto@toto-M2N6-XE ~ $ lsmod 
Module                  Size  Used by
arc4                   12608  2 
rtl8187                64909  0 
mac80211              626489  1 rtl8187
cfg80211              484040  2 mac80211,rtl8187
eeprom_93cx6           13344  1 rtl8187
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
dm_crypt               23177  1

---

