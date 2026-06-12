---
title: "i am so close...please help. installed inf driver recognizes device but no network co"
date: 2008-12-02
forum: Hardware
---

### Post by curiouscustomer on 2008-12-02
ok

installed ndisgtk 
installed linksys inf driver file
hardware testing recognizes linksys network card

but no netowrk connections in network tools

i am so close please please please help.

please i am begging you.

---

### Post by Idefix82 on 2008-12-02
So what card are we talking about here? What is the output of
```
lshw -C network
```
Also, I am assuming that you are running Ubuntu 8.10?

---

### Post by curiouscustomer on 2008-12-02
actually i am mistaken. ubuntu is recognizing a broadcom network card. how weird is that.

---

### Post by curiouscustomer on 2008-12-02
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4a:4a:30:79:a4:c8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

yes 8.10

---

### Post by curiouscustomer on 2008-12-02
it would be silly to install the broadcom driver i assume.
and linksys support insisted i remove the card until i find the right driver.

---

### Post by curiouscustomer on 2008-12-02
apparantly i have to download the broadcom bcm4318 firmware.

if i can find it.

---

### Post by sergiom99 on 2008-12-02
a forums search for "BCM4318 [AirForce One 54g]" (your network card)
showed this useful threads:
[http://ubuntuforums.org/showthread.php?t=963978&highlight=BCM4318+%5BAirForce+54g%5D](http://ubuntuforums.org/showthread.php?t=963978&highlight=BCM4318+%5BAirForce+54g%5D)
[http://ubuntuforums.org/showthread.php?t=880218&highlight=BCM4318+%5BAirForce+54g%5D](http://ubuntuforums.org/showthread.php?t=880218&highlight=BCM4318+%5BAirForce+54g%5D)

All the results>
[http://ubuntuforums.org/search.php?searchid=52563689](http://ubuntuforums.org/search.php?searchid=52563689)

make sure you have the latest packages:
```
 sudo apt-get update && sudo apt-get safe-upgrade
```
Good luck!

---

