---
title: "Lose Network Abilities on Upgrade"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by .:Justus:. on 2009-03-09
I just did a fresh install of Xubuntu Intrepid 8.10 and after setting up my wireless connection i have 220 updates ready, naturally i want to update...
Yet, when i finish the updates my network card drivers are uninstalled  and my wired connection doesn´t work, forcing me to completely reinstall xubuntu again in order to use the internet.
Frankly, i am unable to update my system since it results in my network capabilities failing.
What can i do?? Am i missing out on something or is this normal/ is there a simple fix for this? :(
______________________

Help is greatly appreciated ~ Thank you in advance!

---

### Post by cariboo on 2009-03-09
A little more information would be helpful, what chipset does your wireless device use. If you don't know open a Applications-->Accessories-->Termianl and type:

```
sudo lshw -C network
```

Paste the output in your next post.

Jim

---

### Post by .:Justus:. on 2009-03-09
> **cariboo907 said:**
> A little more information would be helpful, what chipset does your wireless device use. If you don't know open a Applications-->Accessories-->Termianl and type:

```
sudo lshw -C network
```

Paste the output in your next post.

Jim

Thanks Jim, im on an AAO this is the output:

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.2.100 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

________

Also, I´m not too experienced with *buntu but a google search came up with several people who had this bug, and they were all using different setups, dunno if that helps you.

---

### Post by khelben1979 on 2009-03-09
Are you able to install the driver manually from Synaptic which refers to the wireless network driver after all the updates has been installed?

This would require that you don't need a wireless connection in order to install the driver.

---

### Post by Neo_The_User on 2009-03-09
Take out your MAC address in your post. You don't want people like me looking at that ):P

---

### Post by .:Justus:. on 2009-03-09
> **khelben1979 said:**
> Are you able to install the driver manually from Synaptic which refers to the wireless network driver after all the updates has been installed?

This would require that you don't need a wireless connection in order to install the driver.

Yes i am, but the thing is as soon as i restart after the updates, that´s when my network config is deleted, as in the drivers are gone and nothing works. So right after the updates i can continue using everything until the updates are applied after the reboot.

> **Neo_The_User said:**
> Take out your MAC address in your post. You don't want people like me looking at that ):P
ups thanks^^

---

### Post by .:Justus:. on 2009-03-10
Never mind solved it, was a kernel problem.

---

