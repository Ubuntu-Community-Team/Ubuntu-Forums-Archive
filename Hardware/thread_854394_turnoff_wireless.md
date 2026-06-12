---
title: "turnoff wireless"
date: 2008-07-09
forum: Hardware
---

### Post by madubuntuer on 2008-07-09
hi 
I have a acer 5633WLMI laptop and was wondering if I could prevent ubuntu from turning on the wireless automatically when it boots? So I want to manually turn it on when I need it. Ideally I won't have to type in the encryption key everytime I connect to my local wireless.

 *-network               
       description: Ethernet interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:c8:a6:48
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=0.0 0:0 () latency=0 link=no module=ipw3945 multicast=yes

---

### Post by unoodles on 2008-07-09
Does your computer have a killswitch? If so just turn it off then turn it back on when you need it.

Another quick but dirty hack would be to blacklist the driver (from the looks of it you are using the ipw3945 driver) and just type:
sudo modprobe ipw3945
when you want to start it.

---

### Post by stchman on 2008-07-09
> **madubuntuer said:**
> hi 
I have a acer 5633WLMI laptop and was wondering if I could prevent ubuntu from turning on the wireless automatically when it boots? So I want to manually turn it on when I need it. Ideally I won't have to type in the encryption key everytime I connect to my local wireless.

 *-network               
       description: Ethernet interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:c8:a6:48
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=0.0 0:0 () latency=0 link=no module=ipw3945 multicast=yes

Most laptops have a wireless on/off switch in the front or side.  Turn it off.

What version of Ubuntu are you running?  Hardy has the login password and keyring password match.

---

