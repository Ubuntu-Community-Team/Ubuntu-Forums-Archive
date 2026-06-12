---
title: "Ubuntu 15.10 bluetooth support"
date: 2015-12-14
forum: Hardware
---

### Post by Kusho on 2015-12-14
When I go to System Settings and select Bluetooth it says bluetooth is disabled.  I click On but nothing happens.  It never shows up on my top bar and nothing happpens.  All the help files i see say to click the bluetooth icon on the top bar but its not there.  Thanks for any help.

---

### Post by weatherman2 on 2015-12-14
Could be no bluetooth driver has been loaded for your computer's bluetooth card.  This is not uncommon.

What kind of computer is it?  Make/model?

Please give the output of these terminal commands (Ctrl Alt t to open a terminal):

```

sudo lshw -C network
lsusb
lspci
rfkill list all
dmesg | grep -i bluet

```

---

### Post by Kusho on 2015-12-15
Asus EEE Pc 904HA

  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: b0
       serial: 00:24:8c:09:15:10
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 01
       serial: 00:22:43:58:6b:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=4.2.0-19-generic firmware=N/A ip=10.1.1.228 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:fbef0000-fbefffff
tom@tom-1000H:~$ \^

The Bluetooth adapter is a usb dongle...  no idea the make or model.  its a small little thing that i bought back when i bought the computer maybe 5 years ago.  It worked in a previous version of Ubuntu...  dont remember which version sorry.

---

