---
title: "[SOLVED] Internet not working."
date: 2008-10-03
forum: General Help
---

### Post by rmjohnson144 on 2008-10-03
I installed Ubuntu on my cousins computer and his linksys wireless usb adapter wasn't recognized nor did Linksys have Linux drivers.

I then hooked up my D-Link wireless ethernet adapter.  but it didn't auto-recognize it.  I went to network manager and couldn't find it.

Is there a simple way to enable my eth0 or whatever it's called?
-=Mark=-

---

### Post by nitecon on 2008-10-03
Wireless nic's are generally wlan0 and wired nic's eth0 or eth1 depending on how many of them you have.

Since he has a linksys device this might be what you are looking for :[http://linuxwireless.org/en/users/Drivers/zd1211rw](http://linuxwireless.org/en/users/Drivers/zd1211rw)

Although if you can connect to the internet with wired internet I would suggest first checking to see if the hardware device driver utility can automatically fetch the driver/firmware for you.  If you are in ubuntu look under SYSTEM Menu > Administration > Hardware drivers.

---

### Post by rmjohnson144 on 2008-10-03
well, I just reinstalled Ubuntu and still no internet.  From what I can tell iot's not even installing the NIC port?  I'm installing this on a old Dell.  It has a broadcomm nic port I believe.  

Anyone know what else I can do?
-=Mark=-

---

### Post by rmjohnson144 on 2008-10-04
OK, I forgot I disabled the nic port a while back when using the usb nic.  after I enabled the nic port it seems to have installed, but I still can't get online.  

I went to the network manager and it has an option to "connect to a 802.1x protected wired network"  I type in my ssid name in the "Network Name" field and hit connect only to get an error of, "A passphrase or encryption key is required to access the network 'dlink'"  I have no clues as to what key it wants or where to enter it.  The EAP method is set on "PEAP" (I have no clues what this is) and the rest off.  My router is set to no encrytion. 

I'm not sure what else to try.
-=Mark=-

---

### Post by rmjohnson144 on 2008-10-04
woot, I got it working.  It turns out I needed to manually set my wireless adapter up from firefox.   I needed to set the SSID name there instead of within linux.  

strange, but it works!!!
-=Mark=-
ps, I forgot to mention I was using the Dlink DGL-3420 Wireless Ethernet Adapter.

---

