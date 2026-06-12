---
title: "Ethernet no longer working"
date: 2011-08-27
forum: Hardware
---

### Post by tkoopa on 2011-08-27
My onboard network card stopped working and I can't figure if it's broken or not.

I have a mythbuntu server machine ( 10.04.03 ) running with all the latest updates. It usually runs 24/7, but I powered it down for a week whilst on vacation. 

When I switched it back on it no can no longer use the onboard ethernet. I tried changing the port on the router ( the light turns on orange on the router ( not green ), which normally means it's not detecting gigabit speed.

sudo lspci -v shows me it's detected:

```
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller
	Subsystem: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at c800 [size=256]
	Expansion ROM at fe9c0000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: sky2
	Kernel modules: sky2
```

sudo lshw -C network gives me this:


```

       *-network DISABLED      
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fe9fc000-fe9fffff ioport:c800(size=256) memory:fe9c0000-fe9dffff(prefetchable)
```

As you can see, there is no mac address ( I didn't edit the result to hide it )

ifconfig however shows no eth0, just l0.

I plugged in a usb wi-fi adapter and that works fine. 
I also booted a natty live-cd I had lying around with the same result ( no eth0)

Whilst googling I read a bit on a windows forum about the card going to sleep, could this be the problem ( as it's detected ) ? and if so how do I wake it up ? Or is it dead and therefore should I just buy a new network card? 

Thanks in advance for any suggestions

---

### Post by tkoopa on 2011-08-27
Found a solution by forcing the mac address (it was reported as 00:00:00:00:00:00 ) thanks to [http://ubuntuforums.org/showthread.php?t=1639063#9](http://ubuntuforums.org/showthread.php?t=1639063#9)

For 10.04.03 I had to add this to /etc/rc.local for it work ( replacing 00:00:00:00:00:00 with the correct mac address ):

```
ifconfig eth0 hw ether 00:00:00:00:00:00
restart network-manager
```

---

