---
title: "Upgrade to 8.10 broke my wifi."
date: 2008-11-04
forum: Hardware
---

### Post by nathacof on 2008-11-04
Compaq Presario, F756NR:

Previously I was using the MadWifi drivers for my Atheros chipset to enable wifi on my laptop.

After hearing that 8.10 supported the ath9k module I decided to go for the upgrade, due to the fact that any time I would upgrade Ubuntu (IE: the kernel) I would need to reinstall the madwifi drivers which was a bit of a pain.

Well the upgrade appeared to go well, and the drivers appear to be loaded, however I am unable to bring up my wireless nic.

The ath_pci drivers appear to be loaded without issue, but if I run iwconfig it doesn't show any adapters which support wireless.

lspci shows the chipset as:

Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Looking at the ath9k site, I don't see this model listed.

At this point, I've tried reinstalling the MadWifi drivers which caused my laptop to whitescreen (that's the best way I can describe it, looked like problems with the video output).

So I've attempted to uninstall the MadWifi drivers by running 

sudo make uninstall


The Atheros driver still doesn't pick up the wifi card. I feel like I shouldn't even have attempted this upgrade at this point.

Anyone out there have this working? ](*,)]

Sorry I can't provide more information I'm posting this from my girlfriends laptop.

Any help is greatly appreciated.

---

### Post by nathacof on 2008-11-04
I plugged this sucker in so I've got some more information for your guys:

```
Installing MadWifi...OK
Loading kernel module...OK
Adding ath_pci to /etc/modules...OK
It seems that the driver did not detect compatible hardware.
Please try to connect to an AP and post the output of
sudo ./madwifi.sh --info to the forum.
nathacof@nathacof-laptop:~$
```

```

nathacof@nathacof-laptop:~$ sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux nathacof-laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: fast devsel, IRQ 19
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Kernel modules: ath_pci

ath_pci               218296  0 
wlan                  239984  1 ath_pci
ath_hal               259552  1 ath_pci
[  172.756820] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[  172.756840] ath_pci 0000:03:00.0: setting latency timer to 64
[  172.756860] ath_pci: HAL doesn't support MAC revision 0xe2
[  172.756873] ath_pci 0000:03:00.0: PCI INT A disabled
[   20.350652] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   20.350662] ath_pci 0000:03:00.0: setting latency timer to 64
[   20.350679] ath_pci: HAL doesn't support MAC revision 0xe2
[   20.350691] ath_pci 0000:03:00.0: PCI INT A disabled
wifi0: 0 ath0: 0
nathacof@nathacof-laptop:~$ nathacof@nathacof-laptop:~$ sudo ./madwifi.sh --info
Found at least one Atheros device.
Linux nathacof-laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 137a
	Flags: fast devsel, IRQ 19
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Kernel modules: ath_pci

ath_pci               218296  0 
wlan                  239984  1 ath_pci
ath_hal               259552  1 ath_pci
[  172.756820] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[  172.756840] ath_pci 0000:03:00.0: setting latency timer to 64
[  172.756860] ath_pci: HAL doesn't support MAC revision 0xe2
[  172.756873] ath_pci 0000:03:00.0: PCI INT A disabled
[   20.350652] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   20.350662] ath_pci 0000:03:00.0: setting latency timer to 64
[   20.350679] ath_pci: HAL doesn't support MAC revision 0xe2
[   20.350691] ath_pci 0000:03:00.0: PCI INT A disabled
wifi0: 0 ath0: 0
nathacof@nathacof-laptop:~$

```

This worked without issue in 8.04. :'(

```

nathacof@nathacof-laptop:~$ iwconfig
lo        no wireless extensions.

eth88     no wireless extensions.

pan0      no wireless extensions.

nathacof@nathacof-laptop:~$ 

```

---

### Post by nathacof on 2008-11-04
Fixed:

rmmod ath_pci ath_hal
insmod ath5k

---

