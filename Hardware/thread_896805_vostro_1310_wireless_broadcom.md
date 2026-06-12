---
title: "vostro 1310 wireless broadcom"
date: 2008-08-21
forum: Hardware
---

### Post by rpwaf on 2008-08-21
Hi:
Just bought a vostro 1310. I've manage to make everything works except for the wireless default Dell network adaptor. This system is quite new so I may be normal to have difficulties make it work.

Here's what I've try:

[http://ubuntuforums.org/showthread.php?t=880218&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=880218&highlight=broadcom)
and
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
This also does'nt work even if I use the driver that comes with the vista os.
I've try step 2e and I also try as mentioned the driver that comes with vista. I've also try to build from source ndiswrapper.

I'm a bit frustated so I hope community can help. 

Here's some info you might need:
Dell Vostro 1310 

Wireless Brand and Model: 06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
Wireless Chipset: 06:00.0 0280: 14e4:4315 (rev 01)
Ubuntu Version: Ubuntu 8.04.1


Thanks for your help.

---

### Post by falcon61102 on 2008-08-21
Code you run the following command in the terminal and post the results:
```
sudo lshw -C network
```

This will provide a few more details on your hardware and drivers.

---

### Post by rpwaf on 2008-08-21
t@darkstar:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:c4:c0:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:a2:07:52
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.008.00-NAPI duplex=full ip=192.168.2.12 latency=0 link=yes module=r8168 multicast=yes port=twisted pair speed=100MB/s

I dont know a lot about wifi and linux and if I rmmod of wl so ndiswrapper can take over my wifi led on the pc goes off and then the module=xxx is no more there.

thanks

---

### Post by Ayuthia on 2008-08-21
> **rpwaf said:**
> t@darkstar:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:c4:c0:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:a2:07:52
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.008.00-NAPI duplex=full ip=192.168.2.12 latency=0 link=yes module=r8168 multicast=yes port=twisted pair speed=100MB/s

I dont know a lot about wifi and linux and if I rmmod of wl so ndiswrapper can take over my wifi led on the pc goes off and then the module=xxx is no more there.

thanks

Can you provide the results of the folowing from the Terminal:
```
lsmod|grep -i -e b43 -e bcm43xx -e wl -e ssb -e ndiswrapper
```
I would also like to see if you have the wl driver:
```
sudo updatedb
locate wl.ko
```
The updatedb command will update the search database and then the second command will try and find the file.

Your card should work with the wl module and I thought that I seen that it is in linux-restricted modules for your chipset.

---

### Post by falcon61102 on 2008-08-21
Also make sure that after you remove wl, you have to start ndiswrapper with:
```
sudo modprobe ndiswrapper
```

And you may have to blacklist wl for that to work correctly.

---

### Post by rpwaf on 2008-08-22
root@darkstar:~# lsmod|grep -i -e b43 -e bcm43xx -e wl -e ssb -e ndiswrapper
ssb                    34308  1 b44
ndiswrapper           192920  0 
wl                   1062164  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd


root@darkstar:~# locate wl.ko
/home/rp/Desktop/hybrid_wl/.wl.ko.cmd
/home/rp/Desktop/hybrid_wl/wl.ko

---

### Post by rpwaf on 2008-08-22
Hi Falcon:
finally I've download the driver for windows XP from the Dell website.

I've reload that in ndiswrapper 

I've added wl to the blacklist and reboot

Now it looks like it work! 

Is there a gui app to scan for wifi network.

I've read about wlassistant but is there something integrated in ubuntu. I wonder why apparently the network manager does not do that.

My home network is wpa and since I was connected 5 minutes ago it disconnect and ask me for my passphrase it's a little anoying so I'm not completly satisfied. ;-)

Any clue to fix that?

Thanks

---

### Post by rpwaf on 2008-08-24
I see lots of people having the same kind of issue with broadcom ndiswrapper and wpa. Some says its the broadcom card that is shitty.

I will try get the intel card instead of the default dell one. 

thanks guys.

---

