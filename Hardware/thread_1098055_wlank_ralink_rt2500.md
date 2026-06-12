---
title: "wlank ralink rt2500"
date: 2009-03-16
forum: Hardware
---

### Post by DefaultUser123 on 2009-03-16
I'm trying to get my wlan(on a medion md8800) to work on Kubuntu 8.10 but I've had no luck so far :/

Done that 
[http://www.unixboard.de/vb3/showthread.php?t=17269](http://www.unixboard.de/vb3/showthread.php?t=17269)
Basically says how to install the driver, which I did without any problem. Then I typed in lshw -C network and got the following:
```
  *-network
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1d:92:73:a0:a5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 module=e1000e multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 4a:6b:c0:44:76:fe
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

``` 

Just didn't figure out yet how to activate it :/

iwconfig says
```
lo    no wirless extensions.
eth0    no wirless extensions.
pan0    no wirless extensions.
```

thx  for help

---

