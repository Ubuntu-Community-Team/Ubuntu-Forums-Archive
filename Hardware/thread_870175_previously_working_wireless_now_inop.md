---
title: "previously working wireless now inop"
date: 2008-07-25
forum: Hardware
---

### Post by goldenbough on 2008-07-25
I updated my system and after doing this (whether or not this is related is unclear) I lost my wireless capability on my computer.  When I right click on the network connection icon, there isn't even a box for wireless, which I should be able to click on and off.

---

### Post by phidia on 2008-07-25
What type/model wireless card does your computer have
> lshw -C network and how did you get it working in the 1st place?

---

### Post by goldenbough on 2008-07-25
AR5006EG 802.11 b/g Wireless PCI Express Adapter


sudo apt-get install build-essential
wget [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)
tar xfz madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007
sudo make
sudo make install
sudo modprobe ath_pci

---

### Post by phidia on 2008-07-25
I think there has been a recent kernel update-when that happens modules that are hand built have to be built again for the new kernel. 
Just cd to the madwif directory and run the last two commands from your post again. I believe that will do it.

---

### Post by goldenbough on 2008-07-25
When I get to the last line sudo modprobe ath_pci it throws the error:

FATAL: Error inserting ath_pci (/lib/modules/2.6.22-15-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by markusd112 on 2008-08-24
> **goldenbough said:**
> When I get to the last line sudo modprobe ath_pci it throws the error:

FATAL: Error inserting ath_pci (/lib/modules/2.6.22-15-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I have exactly the same problem: I normally use an UMTS internet connection, but today I want to access the internet via WLAN, but it doesn't work anymore...

Do you get it working?

Thanks,

Markus

---

