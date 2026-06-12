---
title: "Compaq C700 w/Ubuntu 8.04 Wireless Stopped after updates"
date: 2008-06-08
forum: Hardware
---

### Post by phlaw23 on 2008-06-08
My wireless (atheros Ar5006EG) had been working great, yesterday I installed updates on my laptop and after I rebooted my wireless no longer worked?

I am not an expert with Ubuntu so I am lost.

I know when I originally got it working I did the following:

First get the patched madwifi drivers from the site and extract them to some place (maybe your desktop) 
You need to compile these drivers, so you must sudo apt-get install build-essential. 
Then cd into that directory which you extracted recently and do a make, sudo make install 
Then add the following two lines to this file /etc/modules 
ath_pci
wlan_scan_staThen make sure that you disabled Atheros from System > Administration > Hardware Drivers (also called Restricted drivers management). If you don’t disable this, the modules which you added in the previous lines wont be loaded. 
Then restart your system to find a new device named ath0 (when you ifconfig) 


***  I have verified all of these steps, and it still does not work.

Thanks

---

