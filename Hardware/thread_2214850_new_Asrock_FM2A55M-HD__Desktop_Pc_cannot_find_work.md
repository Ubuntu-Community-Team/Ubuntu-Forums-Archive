---
title: "new Asrock FM2A55M-HD  Desktop Pc cannot find working router"
date: 2014-04-03
forum: Hardware
---

### Post by jackson21 on 2014-04-03
Hi, All,
My running system Desktop PC with Asrock  mainboard and
Fritzel router have never let me down in the last 4 years.
With several Ubuntu distros on my harddisk, no problems whatsoever.

But!!!! have set up a brand new PC with new motherboard ASROCK FM2A55-HD,
Gblan, AMD+A10-7700 4x3.40 GHz boxed


When I exchanged  for the new PC. and plugged in the router, 
Super graphics, new Ubuntu 14.04 Beta,   _but no connection to the router_.

Have replaced and configured the router for a new one, 
but my new Pc doesn't find   the router.

At boot up , no leds are on  at netcable   plug-in

Ubuntu says:  "no interface  


Any help is welcome



jackson

---

### Post by varunendra on 2014-04-05
Please show us the outputs of -
```
uname -mr
sudo lshw -numeric -C network
```

And if you have an alternative way to connect to internet, please install 'ethtool'-
```
sudo apt-get install ethtool
```
Then post back the output of -
```
sudo ethtool eth0
```
..assuming your Ethernet interface is "eth0". If it has a different name, please change it accordingly. Of course this is not applicable if it is not detected at all, in which case, check your BIOS to make sure it is enabled there. Also see if there is a feature called "IOMMU" in the BIOS. If there is, try enabling it.

---

### Post by jackson21 on 2014-04-06
Thank you very much,
I have the solution !!!  a network pci card , I plugged the router in and  BINGO !!!!

---

