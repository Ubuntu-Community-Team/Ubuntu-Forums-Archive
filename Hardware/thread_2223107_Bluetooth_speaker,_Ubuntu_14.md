---
title: "Bluetooth speaker, Ubuntu 14"
date: 2014-05-09
forum: Hardware
---

### Post by pmorton on 2014-05-09
I am unable to get a bluetooth connection to a Bose Mini-link speaker from My Lenovo X1 Carbon laptop. 

lsusb shows that the bluetooth adaptor is "Broadcom Corp. BCM20702 Bluetooth 4.0". Bluetooth device set up finds the speaker, but when i try to connect to it, it vanishes from the device listing. Is there a problem with the kernel driver for this device, does anyone know?

---

### Post by BKTech86 on 2014-08-11
I have the same problem with my HP Envy 15.  Trying to connect to my bose or any bluetooth audio device, it sees it, but then fails during the pairing and then can never find it again.  Surprised to see that such a basic function wouldn't be supported in Ubuntu 14 when it used to work fine in previous versions.  Nonetheless, very frustrating.  Does anyone know how to remedy this problem?

---

### Post by weatherman2 on 2014-08-11
I have paired several BT speakers in Ubuntu 14.04, so the "basic function" certainly works in general. It wasn't completely straightforward though.  I think I had to separately "enable" the BT device even after it had been paired, which was frustrating.

---

### Post by pmorton on 2014-08-18
Updating the kernel (I'm using 3.14.4-031404) sorted it for me. Now I have no further problem with bluetooth and the Bose Mini-link.

---

