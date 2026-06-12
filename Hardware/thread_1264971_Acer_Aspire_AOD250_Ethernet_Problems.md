---
title: "Acer Aspire AOD250 Ethernet Problems"
date: 2009-09-12
forum: Hardware
---

### Post by linuxnoob53108 on 2009-09-12
I went through the fix that is listed on the AspireOneAOD250 Community Ubuntu Documentation Page [HERE]("https://help.ubuntu.com/community/AspireOneAOD250#Install%20Wired%20Network%20Driver").

but I still can't seem to connect to the wired connection, here is the output to my connection information

```
jc@jc-netbook:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2c:4f:61:02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 62:7c:25:3b:33:9b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Any help would be appreciated!

Thanks :)

---

### Post by mikewhatever on 2009-09-12
Can you post the output of **lsmod | grep atl1e**. It looks like the module is not loaded. Be sure to run the last command to load the module.
sudo modprobe atl1e

---

### Post by linuxnoob53108 on 2009-09-12
here is what it looks like when I run the final command during the install
```
jc@jc-netbook:~/Ethernet - Network Stuff$ sudo modprobe atl1e
jc@jc-netbook:~/Ethernet - Network Stuff$ 

```

here is the output from the command you suggested
```
jc@jc-netbook:~/Ethernet - Network Stuff$ lsmod|grep atl1e
atl1e                  40212  0
```

Thanks for your help.

---

### Post by linuxnoob53108 on 2009-09-12
Got it! Just needed to use make clean then sudo make install and reboot, this forum is a savior!!

---

### Post by sam-moss on 2009-11-26
Ah thanks Linuxnoob. I was having a similar problem but I did what you said "make clean then sudo make install and reboot" and it worked!
 
Been racking my brains out trying to solve the problem. Thanks again.
 
Sam
 
To learn more about the fat burning furnace then you must read [http://weightwoo.com/fat-burning-furnace](http://weightwoo.com/fat-burning-furnace) now.

---

