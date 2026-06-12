---
title: "Help!!"
date: 2009-02-01
forum: Hardware
---

### Post by rprzybylow on 2009-02-01
I want to love this ubuntu, I am a newbie,  I am taking fedora rat hat 7 at ITT.  I failed two times,  I really want to switch to Linex,  Please help me turn on my wifi.  I have the rest of my life to learn all about linex products.  I will tell everyone I ever meet about Ubuntu. 

My wifi light is on 

Also I have  Dell Latitude D520 



To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

robert@robert-laptop:~$ sudo lshw -C network
[sudo] password for robert: 
Sorry, try again.
[sudo] password for robert: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:71:c0:45
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:72:b6:8f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 92:f2:98:a7:ed:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Sincerely,

Robert

---

### Post by ajmorris on 2009-02-02
hi there,
if the light is on, then the bcm43xx native linux drivers for your card are active, and you shouldnt need to fiddle with 'ndiswrapper' or anything like that :)
However, that being said, wireless is quite fiddly sometimes, and you might need to have a play around with a few utilities to get it working. Firstly try 'Network Manager' (the network icon in the system tray of GNOME). Then you will want to try 'wicd' (sudo apt-get install wicd). If both of those fail, try using wpa_supplicant. If all three of those fail, then move onto using ndiswrapper. If you need any help with any of the four methods, don't hesitate to ask. I can give you step by step instructions on how to use them :)
(according to your lshw output, your network interface is 'wlan0' - so use that interface when using the four tools above.)


AJ

---

### Post by Ayuthia on 2009-02-02
You might try checking System->Administration->Hardware Drivers to see if there is an option for you for the Broadcom wireless driver.  You should have two options (Broadcom b43 and Broadcom STA).  If you don't see any options, go into Synaptic and install b43-fwcutter.  If you have a working connection in Ubuntu, say yes when it asks to fetch the firmware for you.  Once it is complete, it should ask you to reboot and you should be ready to go.

---

