---
title: "WIFI - N Mode not working (only G) on Acer Aspire 4752G"
date: 2012-06-23
forum: Hardware
---

### Post by snowweb on 2012-06-23
The Acer Aspire 4752G is equipped with the Acer Nplify 802.11b/g/n wireless card and should connect using N mode when connecting to a router of similar capabilities.

The router is a ZyXEL P660HN-T1A which is according to the Quick Start Guide, an 802.11n Wireless ADSL2+ 4-port Gateway.

It currently connects in G mode despite having configured the router to use g/n. When I set the router in n only mode, it did connect, but apparently according to the Knetwork manager it used g mode.

```
$ sudo uname -a
Linux aspire-ubuntu 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
``````
$ sudo lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n
``````
$ nm-tool
                                                                                                                                                      
NetworkManager Tool                                                                                                                                   
                                                                                                                                                      
State: connected (global)                                                                                                                             
                                                                                                                                                      
- Device: eth0 -----------------------------------------------------------------                                                                      
  Type:              Wired                                                                                                                            
  Driver:            tg3                                                                                                                              
  State:             unavailable                                                                                                                      
  Default:           no                                                                                                                               
  HW Address:        20:6A:8A:6F:8B:CA                                                                                                                
                                                                                                                                                      
  Capabilities:                                                                                                                                       
    Carrier Detect:  yes                                                                                                                              
                                                                                                                                                      
  Wired Properties                                                                                                                                    
    Carrier:         off                                                                                                                              
                                                                                                                                                      
                                                                                                                                                      
- Device: eth2  [linux-house] --------------------------------------------------                                                                      
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        7C:E9:D3:15:40:79

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *linux-house:    Infra, CC:5D:4E:F2:1B:18, Freq 2422 MHz, Rate 0 Mb/s, Strength 100 WPA WPA2
```

```
$ lshw
...
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f3a00000-f3afffff
           *-network
                description: Wireless interface
                product: BCM43227 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth2
                version: 00
                serial: 7c:e9:d3:15:40:79
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.6 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f3a00000-f3a03fff
...
```


Does anyone have any ideas?

Thanks.

Peter

---

