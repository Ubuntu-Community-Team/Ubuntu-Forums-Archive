---
title: "need help replacing ath9k with madwifi driver"
date: 2009-06-17
forum: Hardware
---

### Post by n1ght28 on 2009-06-17
Hey,

I have a asus eeepc 100HE which has an Atheros AW-NE771 wifi card, the driveri'm using is ath9k, which is pretty pants, it keeps diconnecting after about an hour of use so i'm trying to install the madwifi-ng driver i have followed these steps

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
sudo modprobe ath_pci
```

and i have amended /etc/modules to include ath_pci so its now
```

fuse
lp
ath_pci
```

but still the output from  sudo lshw -C network is
```

 *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:71:da:fc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=10.0.0.5 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:cc:5e:27:ff:a5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


obviously i need to unload the old ath9k driver but i'm a total newbie and need some advice on doing this, any such advice and explanation of any commands needed would be greatly appreciated,

Thanks,

---

