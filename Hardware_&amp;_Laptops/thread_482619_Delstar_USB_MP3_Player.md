---
title: "Delstar USB MP3 Player"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by Super TWiT on 2007-06-23
I bought this mp3 player:  [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2191202&CatId=2474](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2191202&CatId=2474)

When I plug it into my computer nothing happens.  I have already configured the device to show up as a normal thumb drive.  I cannot download new firmware because Delstar's website is under construction. On Windows it says the device is a generic usb device.  I have tried running mtp-detect in the terminal but it that no mtp devices were found.  The manual says it is compatible with Linux "Reseat" 8.0.  I think this is a typo though.  I believe it is one of these kinds of mp3 players [http://en.wikipedia.org/wiki/S1_MP3_Player](http://en.wikipedia.org/wiki/S1_MP3_Player).  However, it says these devices work with linux.  I have typed dmesg into a command line after unplugging all other usb devices, this has to be the mp3 player.  ```
 2232.282399] usb 5-1: new high speed USB device using ehci_hcd and address 18
[ 2233.811946] usb 5-1: new high speed USB device using ehci_hcd and address 27
[ 2236.134708] usb 5-1: new high speed USB device using ehci_hcd and address 41
[ 2236.712403] usb 5-1: new high speed USB device using ehci_hcd and address 44
[ 2237.607386] usb 5-1: new high speed USB device using ehci_hcd and address 49
[ 2237.860282] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2237.860299] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2238.629082] usb 5-1: new high speed USB device using ehci_hcd and address 51
[ 2239.206785] usb 5-1: new high speed USB device using ehci_hcd and address 54
[ 2240.577685] usb 5-1: new high speed USB device using ehci_hcd and address 62
[ 2240.996741] usb 5-1: new high speed USB device using ehci_hcd and address 64
[ 2241.891722] usb 5-1: new high speed USB device using ehci_hcd and address 69
[ 2242.469421] usb 5-1: new high speed USB device using ehci_hcd and address 72
[ 2242.888472] usb 5-1: new high speed USB device using ehci_hcd and address 74
[ 2243.466174] usb 5-1: new high speed USB device using ehci_hcd and address 77
[ 2244.519796] usb 5-1: new high speed USB device using ehci_hcd and address 83
[ 2246.366629] usb 5-1: new high speed USB device using ehci_hcd and address 94
[ 2248.213469] usb 5-1: new high speed USB device using ehci_hcd and address 105
[ 2264.578553] usb 5-1: new high speed USB device using ehci_hcd and address 122
[ 2264.838966] usb 5-1: new high speed USB device using ehci_hcd and address 123
[ 2265.575305] usb 5-1: new high speed USB device using ehci_hcd and address 127
[ 2265.828200] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2265.828214] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2267.390229] usb 5-1: new high speed USB device using ehci_hcd and address 8
[ 2268.602479] usb 5-1: new high speed USB device using ehci_hcd and address 15
[ 2269.180177] usb 5-1: new high speed USB device using ehci_hcd and address 18
[ 2269.599230] usb 5-1: new high speed USB device using ehci_hcd and address 20
[ 2270.176931] usb 5-1: new high speed USB device using ehci_hcd and address 23
[ 2270.437342] usb 5-1: new high speed USB device using ehci_hcd and address 24
[ 2270.690277] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2270.690296] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2271.776317] usb 5-1: new high speed USB device using ehci_hcd and address 28
[ 2272.988589] usb 5-1: new high speed USB device using ehci_hcd and address 35
[ 2273.883568] usb 5-1: new high speed USB device using ehci_hcd and address 40
[ 2274.619904] usb 5-1: new high speed USB device using ehci_hcd and address 44
[ 2276.149462] usb 5-1: new high speed USB device using ehci_hcd and address 53
[ 2277.044437] usb 5-1: new high speed USB device using ehci_hcd and address 58
[ 2277.297337] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2277.297356] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2278.700701] usb 5-1: new high speed USB device using ehci_hcd and address 64
[ 2279.437041] usb 5-1: new high speed USB device using ehci_hcd and address 68
[ 2279.689935] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2279.689950] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2281.093304] usb 5-1: new high speed USB device using ehci_hcd and address 74
[ 2284.209278] usb 5-1: new high speed USB device using ehci_hcd and address 93
[ 2284.462177] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2284.462196] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2285.072330] usb 5-1: new high speed USB device using ehci_hcd and address 94
[ 2285.967318] usb 5-1: new high speed USB device using ehci_hcd and address 99
[ 2287.655503] usb 5-1: new high speed USB device using ehci_hcd and address 109
[ 2287.908401] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2287.908419] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2288.511049] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2288.511066] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2288.511072] hub 5-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 2289.606103] usb 5-1: new high speed USB device using ehci_hcd and address 115
[ 2290.025160] usb 5-1: new high speed USB device using ehci_hcd and address 117
[ 2290.444217] usb 5-1: new high speed USB device using ehci_hcd and address 119
[ 2290.697109] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2290.697124] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2291.465911] usb 5-1: new high speed USB device using ehci_hcd and address 121
[ 2291.726321] usb 5-1: new high speed USB device using ehci_hcd and address 122
[ 2292.145380] usb 5-1: new high speed USB device using ehci_hcd and address 124
[ 2293.040361] usb 5-1: new high speed USB device using ehci_hcd and address 3
[ 2293.293259] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2293.293277] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2294.537982] usb 5-1: new high speed USB device using ehci_hcd and address 8
[ 2294.790878] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2294.790947] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2295.718316] usb 5-1: new high speed USB device using ehci_hcd and address 11
[ 2295.971218] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2295.971238] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2298.643719] usb 5-1: new high speed USB device using ehci_hcd and address 25
[ 2301.283764] usb 5-1: new high speed USB device using ehci_hcd and address 41
[ 2301.861462] usb 5-1: new high speed USB device using ehci_hcd and address 44
[ 2302.121877] usb 5-1: new high speed USB device using ehci_hcd and address 45
[ 2302.382287] usb 5-1: new high speed USB device using ehci_hcd and address 46
[ 2302.635185] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2302.635201] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2305.942260] usb 5-1: new high speed USB device using ehci_hcd and address 64
[ 2306.837241] usb 5-1: new high speed USB device using ehci_hcd and address 69
[ 2307.414936] usb 5-1: new high speed USB device using ehci_hcd and address 72
[ 2309.103130] usb 5-1: new high speed USB device using ehci_hcd and address 82
[ 2310.474037] usb 5-1: new high speed USB device using ehci_hcd and address 90
[ 2310.726933] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2310.726949] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2313.240804] usb 5-1: new high speed USB device using ehci_hcd and address 103
[ 2315.246280] usb 5-1: new high speed USB device using ehci_hcd and address 115
```

There were also some entries about usb devices but they were scattered in different places.

---

### Post by Super TWiT on 2007-08-07
Anyone?

---

