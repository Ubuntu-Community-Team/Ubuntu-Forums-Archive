---
title: "Cannot connect to wireless"
date: 2009-10-17
forum: Hardware
---

### Post by Susky on 2009-10-17
New install of Ubuntu 9.10 beta 
Acer Aspire
nm-tool shows wireless disconnected.

caddis-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry limit:63   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

caddis-laptop:~$ lspci
.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Attansic Technology Corp. Atheros 
AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)


john@caddis-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        00:26:5E:03:46:72

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    09FX04128647:    Infra, 00:23:97:59:5D:6D, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    SPIRIT:          Infra, 00:14:6C:4A:4D:0C, Freq 2462 MHz, Rate 54 Mb/s, Strength 92


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             connected
  Default:           yes
  HW Address:        00:23:8B:EB:CB:2B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.5.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.5.1

    DNS:             192.168.5.1

---

