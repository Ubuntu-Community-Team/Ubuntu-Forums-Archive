---
title: "WiFi Not detected anymore?"
date: 2005-11-06
forum: General Help
---

### Post by Shalted on 2005-11-06
A while ago, when I got fed up with Windows, I completly switched my laptop(Toshiba Satellite) from Windows XP home, To the Ubuntu Breezy Badger 5.10 Preview Installation. Before I upgraded it, every thing worked fine, but now, My wifi(Atheros AR5212 802.11abg) card isnt recognized anymore(Before there was an ath0 interface, now there isnt). But in I can see it in the device manager.

Any help would be greatly appriciated.

---

### Post by nightfly on 2005-11-06
If you cannot see ath0 in the Networking applet, then it is due to the kernel module not being loaded.

Open a terminal window and try something like
```
sudo modprobe ath_pci
```

If that has worked for you, consider adding the module to the list of modules that are loaded on startup:
```
sudo echo "ath_pci" >> /etc/modules
```

---

### Post by Shalted on 2005-11-06
Nope, it reports:
```
FATAL: Module ath_pci not found.
```
Any other ideas?

---

### Post by nightfly on 2005-11-06
Please browse the file system and check for this location
 /lib/modules/2.6.12-9-386/madwifi

The kernel version might be slightly different. The above location should exist and contain some kernel modules with the file extension ".ko"

If you happen to find everything in place, then try the following command:
```
sudo modprobe /lib/modules/2.6.12-9-386/madwifi/ath_pci.ko
```
Whereas you should alter the kernel version to be exactly as in your setup.

---

### Post by ttthebear on 2007-11-06
Hi,

I know that my wireless was working with ubuntu desktop.  But I have switched to server due to some problems with xen/nvidia.

So when I changed the driver module is not loading for my atheros card.  what I think has happened is that modprobe cannot find the ath_pci.ko module because it is not in the proper directory.

It is currently here

/lib/modules/2.6.22-14-generic/madwifi/

but I think it should be here

/lib/modules/2.6.22-14-server

My question is can I simply copy the whole directory over to that folder without messing anything up?

Thanks

Tom

---

