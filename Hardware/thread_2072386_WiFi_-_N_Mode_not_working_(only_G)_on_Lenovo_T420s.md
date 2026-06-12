---
title: "WiFi - N Mode not working (only G) on Lenovo T420s"
date: 2012-10-17
forum: Hardware
---

### Post by hicolour on 2012-10-17
Does anyone had similar problems ?


$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"network"  
          Mode:Managed  Frequency:2.412 GHz  Access Point:   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33   Missed beacon:0


nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [network] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    primitivus:      Infra, D8:5D:4C:DF:48:34, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA2
    Docenciak:       Infra, 00:21:27:FF:C5:88, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    PegielWirless:   Infra, 94:0C:6D:AC:49:EC, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    UPC0045511:      Infra, 80:C6:AB:2D:89:20, Freq 2462 MHz,  Rate 54 Mb/s, Strength 78 WPA2
    XPS-KOMPUTER_Network_1: Infra, B0:48:7A:E2:58:0C, Freq 2427 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    GSXR:            Infra, C8:3A:35:4D:D4:F8, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA2
    BytomskaIB:      Infra, 00:18:39:A6:DC:9E, Freq 2457 MHz, Rate 54 Mb/s, Strength 29 WPA2

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             62.179.1.62
    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         off

---

### Post by ahallubuntu on 2012-10-17
What kind of wireless card?  To find out, please show the results of:

```
sudo lshw -C network
```

---

### Post by hicolour on 2012-10-19
*-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-32-generic firmware=18.168.6.1 ip=192.168.1.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:51 memory:f2900000-f2901fff

---

### Post by ahallubuntu on 2012-10-19
There have been issues in some cases with Intel cards not being able to maintain N connections in the newer kernels.  I do not have this problem with Ubuntu 10.04 LTS, but the Intel driver changed after that to a completely different one.

The recommended work-around to force G speeds if N is unreliable was this: 

(copied from another forum):

Add the line

```
options iwlwifi 11n_disable=1
```

to the file /etc/modprobe.d/modprobe.conf .

It could be this option was already set when you installed Ubuntu.  You could check for that in your /etc/modprobe.d directory; if you find the option set there in any file, try removing it (comment out the offending line with a "#" in front), reboot and see how reliable your connections are and if they work at N speed.

---

### Post by hicolour on 2012-10-20
Thanks a lot!

---

